---
title: '[擴充屬性]、[工作清單]、[輸出]、[選項] 視窗'
description: 瞭解如何將 Visual Studio 中的工具視窗相關資訊整合至新的 [選項] 頁面，以及 [屬性] 頁面上的新設定。
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54b78197be71dca9fbabbfded90c4e07660a74db
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995794"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>擴充屬性、工作清單、輸出和選項視窗
您可以存取 Visual Studio 中的任何工具視窗。 本逐步解說將示範如何將工具視窗的相關資訊整合至新的 [ **選項** ] 頁面和 [ **屬性** ] 頁面上的新設定，以及如何寫入 **工作清單** 和 **輸出** 視窗中。

## <a name="prerequisites"></a>必要條件
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它會在 Visual Studio 安裝程式中包含為選用功能。 您也可以稍後再安裝 VS SDK。 如需詳細資訊，請參閱 [安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-tool-window"></a>使用工具視窗建立擴充功能

1. 使用 VSIX 範本來建立名為 **TodoList** 的專案，並新增名為 **TodoWindow** 的自訂工具視窗專案範本。

    > [!NOTE]
    > 如需使用工具視窗建立延伸模組的詳細資訊，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

## <a name="set-up-the-tool-window"></a>設定工具視窗
 加入文字方塊，在其中輸入新的 ToDo 專案、將新專案新增至清單的按鈕，以及顯示清單上專案的 ListBox。

1. 在 *TodoWindow* 中，刪除 UserControl 中的 Button、TextBox 和 StackPanel 控制項。

    > [!NOTE]
    > 這不會刪除 **button1_Click** 的事件處理常式，您將在稍後的步驟中重複使用它。

2. 從 [**工具箱**] 的 [**所有 WPF 控制項**] 區段中，將 **Canvas** 控制項拖曳至方格。

3. 將 **TextBox**、 **Button** 和 **ListBox** 拖曳至畫布。 排列元素，讓 TextBox 和 Button 在相同層級上，而 ListBox 會填滿視窗的其餘部分，如下圖所示。

     ![完成的工具視窗](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. 在 [XAML] 窗格中，尋找按鈕，並將其 [內容] 屬性設定為 [ **新增**]。 藉由新增屬性，將按鈕事件處理常式重新連接至按鈕控制項 `Click="button1_Click"` 。 Canvas 區塊看起來應該像這樣：

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>自訂函式

1. 在 *TodoWindowControl.xaml.cs* 檔案中，新增下列 using 指示詞：

    ```csharp
    using System;
    ```

2. 將公用參考新增至 TodoWindow，並讓 TodoWindowControl 的函式採用 TodoWindow 參數。 程式碼看起來應該像這樣：

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. 在 *TodoWindow.cs* 中，變更 TodoWindowControl 的函式以包含 TodoWindow 參數。 程式碼看起來應該像這樣：

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>建立選項頁面
 您可以在 [ **選項** ] 對話方塊中提供頁面，讓使用者可以變更工具視窗的設定。 建立 [選項] 頁面同時需要一個描述 *TodoListPackage.cs* 或 *TodoListPackage .vb* 檔案中選項和專案的類別。

1. 新增名為 `ToolsOptions.cs`的類別。 讓 `ToolsOptions` 類別繼承自 <xref:Microsoft.VisualStudio.Shell.DialogPage> 。

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. 加入以下 using 指示詞：

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. 本逐步解說中的 [選項] 頁面只會提供一個名為 DaysAhead 的選項。 將名為 **daysAhead** 的私用欄位和名為 **daysAhead** 的屬性新增至 `ToolsOptions` 類別：

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   現在您必須讓專案知道這個選項頁面。

### <a name="make-the-options-page-available-to-users"></a>讓使用者可以使用 [選項] 頁面

1. 在 *TodoWindowPackage.cs* 中，將新增 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 至 `TodoWindowPackage` 類別：

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage 函式的第一個參數是 `ToolsOptions` 您稍早建立之類別的型別。 第二個參數 "ToDo" 是 [ **選項** ] 對話方塊中的類別目錄名稱。 第三個參數 [一般] **是 [選項] 對話方塊** 的子類別目錄名稱，其中會提供 [選項] 頁面。 接下來的兩個參數是字串的資源識別碼;第一個是類別目錄的名稱，而第二個是子類別目錄的名稱。 最後一個參數會決定是否可以使用 automation 來存取此頁面。

     當使用者開啟您的 [選項] 頁面時，它應該會類似下圖。

     ![選項頁面](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     請注意分類 **ToDo** 和子類別目錄 **一般**。

## <a name="make-data-available-to-the-properties-window"></a>將資料提供給屬性視窗
 您可以建立名為 `TodoItem` 的類別，將個別專案的相關資訊儲存在 todo 清單中，藉以建立 todo 清單資訊。

1. 新增名為 `TodoItem.cs`的類別。

     當使用者可以使用工具視窗時，ListBox 中的專案會以 TodoItems 表示。 當使用者在清單方塊中選取其中一個專案時，[ **屬性** ] 視窗會顯示專案的相關資訊。

     若要在 [ **屬性** ] 視窗中提供資料，請將資料轉換成具有兩個特殊屬性（和）的公用屬性 `Description` `Category` 。 `Description` 是出現在 [ **屬性** ] 視窗底部的文字。 `Category` 決定在 [ **屬性** ] 視窗顯示于 [ **分類** ] 視圖時，屬性應出現的位置。 在下圖中，[**屬性**] 視窗是在 [**分類** 視圖] 中，已選取 [ **ToDo 欄位**] 分類中的 [**名稱**] 屬性，而 [**名稱**] 屬性的描述會顯示在視窗底部。

     ![屬性視窗](../extensibility/media/t5properties.png "T5Properties")

2. 在 *TodoItem.cs* 檔案中新增下列 using 指示詞。

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 將 `public` 存取修飾詞加入至類別宣告。

    ```csharp
    public class TodoItem
    {
    }
    ```

     加入兩個屬性： `Name` 和 `DueDate` 。 我們將會進行 `UpdateList()` 和 `CheckForErrors()` 更新版本。

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. 將私用參考加入使用者控制項。 加入接受使用者控制項的函式，以及此 ToDo 專案的名稱。 若要尋找的值 `daysAhead` ，則會取得 [選項] 頁面屬性。

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. 因為類別的實例 `TodoItem` 會儲存在 listbox 中，而 listbox 會呼叫函式 `ToString` ，所以您必須多載函式 `ToString` 。 將下列程式碼加入至 *TodoItem.cs*，在函式之後，以及在類別結尾之前。

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. 在 *TodoWindowControl.xaml.cs* 中，將存根方法加入至 `TodoWindowControl` `CheckForError` 和方法的類別 `UpdateList` 。 將它們放在 System.windows.forms.control.processdialogchar 之後和檔案結尾之前。

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     `CheckForError`方法會呼叫父物件中具有相同名稱的方法，而該方法會檢查是否有任何錯誤發生，並正確地處理它們。 `UpdateList`方法會更新父控制項中的 ListBox; 當 `Name` `DueDate` 這個類別中的和屬性變更時，就會呼叫方法。 這些將在稍後執行。

## <a name="integrate-into-the-properties-window"></a>整合至屬性視窗
 現在，撰寫管理 ListBox 的程式碼，這會系結至 [ **屬性** ] 視窗。

 您必須變更按鈕的 click 處理常式來讀取文字方塊、建立 TodoItem，並將它新增至 ListBox。

1. `button1_Click`以建立新 TodoItem 的程式碼取代現有的函式，並將它新增至 ListBox。 它 `TrackSelection()` 會呼叫，稍後會定義。

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. 在設計檢視選取 ListBox 控制項。 在 [ **屬性** ] 視窗中，按一下 [ **事件處理常式** ] 按鈕，然後尋找 **SelectionChanged** 事件。 在文字方塊中填寫 **listBox_SelectionChanged**。 這麼做會新增 SelectionChanged 處理常式的存根，並將其指派給事件。

3. 實作 `TrackSelection()` 方法。 由於您將需要取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 服務，因此您需要讓 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> TodoWindowControl 可存取。 將下列方法新增至 `TodoWindow` 類別：

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. 將下列 using 指示詞新增至 *TodoWindowControl.xaml.cs*：

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. 填寫 SelectionChanged 處理常式，如下所示：

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. 現在，填寫 TrackSelection 函式，它會提供與 [ **屬性** ] 視窗的整合。 當使用者將專案加入 ListBox 或按一下 ListBox 中的專案時，就會呼叫這個函式。 它會將 ListBox 的內容加入至 SelectionContainer，並將 SelectionContainer 傳遞至 **屬性** 視窗的 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 事件處理常式。 TrackSelection 服務會在使用者介面中追蹤選取的物件 (UI) 並顯示其屬性

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     現在您已經有一個可供 [ **屬性** ] 視窗使用的類別，您可以將 [ **屬性** ] 視窗與 [工具] 視窗整合。 當使用者按一下工具視窗中清單方塊中的專案時，[ **屬性** ] 視窗應該會隨之更新。 同樣地，當使用者變更 [ **屬性** ] 視窗中的 ToDo 專案時，應該更新相關聯的專案。

7. 現在，在 *TodoWindowControl.xaml.cs* 中新增其餘的 UpdateList 函式程式碼。 它應該從 ListBox 中卸載並重新新增修改過的 TodoItem。

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. 測試您的程式碼。 建置此專案並開始偵錯。 實驗實例應會出現。

9. 開啟 [**工具**  >  **選項**] 頁面。 您應該會在左窗格中看到 ToDo 分類。 類別目錄會依字母順序列出，因此請查看 Ts。

10. 在 [ **Todo** 選項] 頁面上，您應該會看到 `DaysAhead` 屬性設定為 **0**。 將它變更為 **2**。

11. 在 [ **視圖]/[其他視窗** ] 功能表上，開啟 [ **TodoWindow**]。 在文字方塊中輸入 **結束** 項，然後按一下 [ **加入**]。

12. 在清單方塊中，您應該會看到比今天晚兩天的日期。

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>將文字新增至 [輸出] 視窗，並將專案加入至工作清單
 在 **工作清單** 中，您會建立工作類型的新物件，然後藉由呼叫其方法，將該工作物件加入至 **工作清單** `Add` 。 若要寫入至 [ **輸出** ] 視窗，您可以呼叫其 `GetPane` 方法來取得窗格物件，然後呼叫 `OutputString` 窗格物件的方法。

1. 在 *TodoWindowControl.xaml.cs* 的方法中 `button1_Click` ，新增程式碼以取得 **輸出** 視窗的 **[一般**] 窗格 (這是預設) ，並寫入其中。 方法看起來應如下所示：

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. 為了將專案加入至工作清單，您需要將嵌套類別加入至 TodoWindowControl 類別。 嵌套類別必須衍生自 <xref:Microsoft.VisualStudio.Shell.TaskProvider> 。 將下列程式碼加入至類別的結尾 `TodoWindowControl` 。

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. 接下來，將的私用參考新增至 `TodoTaskProvider` 類別，並將方法加入至 `CreateProvider()` `TodoWindowControl` 類別。 程式碼看起來應該像這樣：

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Add `ClearError()` （會清除工作清單），並將 `ReportError()` 專案新增至工作清單，以將專案加入至 `TodoWindowControl` 類別。

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. 現在就執行 `CheckForErrors` 方法，如下所示。

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>試做

1. 建置此專案並開始偵錯。 實驗實例隨即出現。

2. 開啟 **TodoWindow** (**查看**  >  **其他 Windows**  >  **TodoWindow**) 。

3. 在文字方塊中輸入內容，然後按一下 [ **新增**]。

     今天的到期日是在清單方塊中新增了2天。 不會產生任何錯誤，且 **工作清單** (**視圖**  >  **工作清單**) 應該沒有任何專案。

4. 現在將 [**工具**  >  **選項**  >  **待辦事項**] 頁面上的設定，從 **2** 變更回 **0**。

5. 在 **TodoWindow** 中輸入其他內容，然後再按一下 [ **新增** ]。 這會觸發錯誤，也會觸發 **工作清單** 中的專案。

     當您加入專案時，初始日期會設定為現在加上2天。

6. 在 [ **View** ] 功能表上，按一下 [ **輸出** ] 以開啟 [ **輸出** ] 視窗。

     請注意，每次新增專案時， **工作清單** 窗格中都會顯示一則訊息。

7. 按一下 ListBox 中的其中一個專案。

     [ **屬性** ] 視窗會顯示專案的兩個屬性。

8. 變更其中一個屬性，然後按 **enter**。

     專案會在清單方塊中更新。
