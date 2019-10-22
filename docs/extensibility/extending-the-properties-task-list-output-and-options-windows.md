---
title: 擴充屬性、工作清單、輸出、選項視窗
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eba2e7cbe6957ea786693f86a728ffa6b4aa2cb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633207"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>擴充屬性、工作清單、輸出和選項視窗
您可以在 Visual Studio 中存取任何工具視窗。 本逐步解說示範如何將工具視窗的相關資訊整合到新的 [**選項**] 頁面，以及 [**屬性**] 頁面上的新設定，以及如何寫入至 [**工作清單**] 和 [**輸出**] 視窗。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始，您不會從下載中心安裝 Visual Studio SDK。 它在 Visual Studio 安裝程式中包含為選擇性功能。 您稍後也可以安裝 VS SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-tool-window"></a>使用工具視窗建立擴充功能

1. 使用 VSIX 範本建立名為**TodoList**的專案，並加入名為**TodoWindow**的自訂工具視窗專案範本。

    > [!NOTE]
    > 如需使用工具視窗建立擴充功能的詳細資訊，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

## <a name="set-up-the-tool-window"></a>設定工具視窗
 加入一個文字方塊，在其中輸入新的待辦事項專案、將新專案加入清單的按鈕，以及顯示清單上專案的 ListBox。

1. 在*TodoWindow*中，刪除 UserControl 中的 Button、TextBox 和 StackPanel 控制項。

    > [!NOTE]
    > 這不會刪除**button1_Click**事件處理常式，您會在稍後的步驟中重複使用它。

2. 從 [**工具箱**] 的 [**所有 WPF 控制項**] 區段，將**畫布**控制項拖曳至方格。

3. 將 [ **TextBox**]、[ **Button**] 和 [ **ListBox** ] 拖曳至畫布。 排列元素，讓文字方塊和按鈕在相同層級上，而 ListBox 會填滿其下方的其餘視窗，如下圖所示。

     ![完成的工具視窗](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. 在 [XAML] 窗格中，尋找 [] 按鈕，並將其 [內容] 屬性設定為 [**新增**]。 藉由加入 `Click="button1_Click"` 屬性，將按鈕事件處理常式重新連接至按鈕控制項。 畫布區塊看起來應該像這樣：

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>自訂構造函式

1. 在*TodoWindowControl.xaml.cs*檔案中，新增下列 using 指示詞：

    ```csharp
    using System;
    ```

2. 將公用參考新增至 TodoWindow，並讓 TodoWindowControl 函數接受 TodoWindow 參數。 程式碼看起來應該像這樣：

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. 在*TodoWindow.cs*中，將 TodoWindowControl 的函式變更為包含 TodoWindow 參數。 程式碼看起來應該像這樣：

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
 您可以在 [**選項**] 對話方塊中提供頁面，讓使用者可以變更工具視窗的設定。 建立選項頁時，需要一個描述選項的類別，以及*TodoListPackage.cs*或*TodoListPackage*檔案中的專案。

1. 新增名為 `ToolsOptions.cs` 的類別。 使 `ToolsOptions` 類別繼承自 <xref:Microsoft.VisualStudio.Shell.DialogPage>。

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. 新增下列 using 指示詞：

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. 本逐步解說中的 [選項] 頁面只會提供一個名為 DaysAhead 的選項。 將名為**daysAhead**的私用欄位和名為**daysAhead**的屬性新增至 `ToolsOptions` 類別：

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   現在您必須讓專案知道這個 [選項] 頁面。

### <a name="make-the-options-page-available-to-users"></a>讓使用者可以使用 [選項] 頁面

1. 在*TodoWindowPackage.cs*中，將 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 新增至 `TodoWindowPackage` 類別：

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage 函數的第一個參數是您稍早建立之類別 `ToolsOptions` 的類型。 第二個參數 "ToDo" 是 [**選項**] 對話方塊中的類別目錄名稱。 第三個參數 "General" 是 [**選項**] 對話方塊的子類別名稱，其中提供 [選項] 頁面。 接下來的兩個參數是字串的資源識別碼;第一個是分類的名稱，而第二個是子類別目錄的名稱。 最後一個參數會決定是否可以使用自動化來存取此頁面。

     當使用者開啟您的 [選項] 頁面時，它應該會類似下圖。

     ![選項頁面](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     請注意類別**ToDo**和子類別目錄的**一般**。

## <a name="make-data-available-to-the-properties-window"></a>將資料提供給屬性視窗
 您可以建立名為 `TodoItem` 的類別，將個別專案的相關資訊儲存在 [待辦事項] 清單中，藉此提供待辦事項清單資訊。

1. 新增名為 `TodoItem.cs` 的類別。

     當使用者可以使用工具視窗時，ListBox 中的專案將會以 TodoItems 表示。 當使用者在 ListBox 中選取其中一個專案時，[**屬性**] 視窗會顯示專案的相關資訊。

     若要讓資料可在 [**屬性**] 視窗中使用，您可以將資料轉換成具有兩個特殊屬性的公用屬性，`Description` 和 `Category`。 `Description` 是顯示在 [**屬性**] 視窗底部的文字。 `Category` 決定當 [**屬性**] 視窗顯示在 [**分類**] 視圖中時，應該顯示內容的位置。 在下圖中，[**屬性**] 視窗是在 [**分類**視圖] 中，選取 [**待辦事項欄位**] 分類中的 [**名稱**] 屬性，而 [**名稱**] 屬性的描述會顯示在視窗的底部。

     ![屬性視窗](../extensibility/media/t5properties.png "T5Properties")

2. 在*TodoItem.cs*檔案中新增下列 using 指示詞。

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 將 `public` 存取修飾詞新增至類別宣告。

    ```csharp
    public class TodoItem
    {
    }
    ```

     新增這兩個屬性，`Name` 和 `DueDate`。 我們將會執行 `UpdateList()`，並在稍後 `CheckForErrors()`。

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

4. 將私用參考新增至使用者控制項。 加入接受使用者控制項和此 ToDo 專案名稱的函式。 若要尋找 `daysAhead` 的值，它會取得 [選項] 頁面屬性。

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

5. 因為 `TodoItem` 類別的實例將會儲存在 ListBox 中，而 ListBox 會呼叫 `ToString` 函式，所以您必須多載 `ToString` 函數。 將下列程式碼新增至*TodoItem.cs*，在函式之後和類別的結尾之前。

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. 在*TodoWindowControl.xaml.cs*中，將 stub 方法新增至 `CheckForError` 和 `UpdateList` 方法的 `TodoWindowControl` 類別。 將它們放在 System.windows.forms.control.processdialogchar 之後和檔案結尾的前面。

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     @No__t_0 方法會呼叫父物件中具有相同名稱的方法，而該方法會檢查是否發生任何錯誤，並正確處理它們。 @No__t_0 方法會更新父控制項中的 ListBox。當此類別中的 `Name` 和 `DueDate` 屬性變更時，會呼叫方法。 稍後將會執行。

## <a name="integrate-into-the-properties-window"></a>整合到屬性視窗
 現在撰寫程式碼來管理清單方塊，這會系結至 [**屬性**] 視窗。

 您必須變更按鈕的 click 處理常式，才能讀取文字方塊、建立 TodoItem，並將它新增至 ListBox。

1. 以建立新 TodoItem 的程式碼取代現有的 `button1_Click` 函式，並將其新增至 ListBox。 它會呼叫 `TrackSelection()`，稍後將會定義。

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

2. 在 設計檢視選取 ListBox 控制項。 在 [**屬性**] 視窗中，按一下 [**事件處理常式**] 按鈕，然後尋找**SelectionChanged**事件。 在文字方塊中填入**listBox_SelectionChanged**。 這麼做會為 SelectionChanged 處理常式新增存根，並將其指派給事件。

3. 實作 `TrackSelection()` 方法。 由於您將需要取得 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 服務，因此您需要讓 TodoWindowControl 可存取 <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>。 將下列方法新增至 `TodoWindow` 類別：

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. 將下列 using 指示詞新增至*TodoWindowControl.xaml.cs*：

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

6. 現在，填入 TrackSelection 函式，此函式會提供與 [**屬性**] 視窗的整合。 當使用者將專案加入 ListBox 或按一下 ListBox 中的專案時，就會呼叫這個函式。 它會將 ListBox 的內容加入至 SelectionContainer，並將 SelectionContainer 傳遞至 [**屬性**] 視窗的 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 事件處理常式。 TrackSelection 服務會在使用者介面（UI）中追蹤選取的物件，並顯示其屬性。

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

     現在您已經有一個 [**屬性**] 視窗可以使用的類別，您可以將 [**屬性**] 視窗與工具視窗整合。 當使用者在工具視窗中按一下清單方塊中的專案時，應該會據以更新 [**屬性**] 視窗。 同樣地，當使用者變更 [**屬性**] 視窗中的 [待辦事項] 專案時，應該更新相關聯的專案。

7. 現在，在*TodoWindowControl.xaml.cs*中新增其餘的 UpdateList 函數程式碼。 它應該會從 ListBox 中卸載並重新加入修改過的 TodoItem。

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. 測試您的程式碼。 建置此專案並開始偵錯。 應該會出現實驗實例。

9. 開啟 **工具**  > **選項** 頁面。 您應該會在左窗格中看到 [ToDo] 分類。 類別目錄會以字母順序列出，因此請查看 Ts 底下的。

10. 在 [**待辦事項**選項] 頁面上，您應該會看到 `DaysAhead` 屬性設定為**0**。 將它變更為**2**。

11. 在 [ **View]/[其他視窗**] 功能表上，開啟 [ **TodoWindow**]。 在文字方塊中輸入**結束**日期，然後按一下 [**新增**]。

12. 在清單方塊中，您應該會看到比今天晚兩天的日期。

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>將文字新增至 輸出 視窗，並將專案加入至 工作清單
 在**工作清單**中，您會建立 task 類型的新物件，然後藉由呼叫其 `Add` 方法，將該工作物件加入至**工作清單**。 若要寫入至 [**輸出**] 視窗，您可以呼叫它的 `GetPane` 方法來取得窗格物件，然後呼叫 pane 物件的 `OutputString` 方法。

1. 在*TodoWindowControl.xaml.cs*的 `button1_Click` 方法中，加入程式碼以取得 [**輸出**] 視窗的 [**一般**] 窗格（這是預設值），並寫入其中。 此方法看起來應該像這樣：

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

2. 若要將專案加入至工作清單，您需要將嵌套類別新增至 TodoWindowControl 類別。 此嵌套類別必須衍生自 <xref:Microsoft.VisualStudio.Shell.TaskProvider>。 將下列程式碼新增至 `TodoWindowControl` 類別的結尾。

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

3. 接下來，將 `TodoTaskProvider` 和 `CreateProvider()` 方法的私用參考新增至 `TodoWindowControl` 類別。 程式碼看起來應該像這樣：

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

4. 新增 `ClearError()`，這會清除工作清單，而 `ReportError()` 會將專案新增至工作清單 `TodoWindowControl` 類別。

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

5. 現在，請執行 `CheckForErrors` 方法，如下所示。

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

## <a name="try-it-out"></a>立即試用

1. 建置此專案並開始偵錯。 實驗實例隨即出現。

2. 開啟**TodoWindow** （**View**  > **其他 Windows**  > **TodoWindow**）。

3. 在文字方塊中輸入內容，然後按一下 [**新增**]。

     今天后2天的到期日會加入清單方塊。 不會產生錯誤，而且**工作清單**（**View**  > **工作清單**）不應該有任何專案。

4. 現在將 [**工具** > **選項**]  >  [**待辦事項**] 頁面上的設定從**2**變更為**0**。

5. 在**TodoWindow**中輸入其他內容，然後再按一下 [**新增**]。 這會觸發錯誤以及**工作清單**中的專案。

     當您加入專案時，初始日期會設定為現在加上2天。

6. 在 [ **View** ] 功能表上，按一下 [**輸出**] 以開啟 [**輸出**] 視窗。

     請注意，每當您加入專案時，[**工作清單**] 窗格中就會顯示一則訊息。

7. 按一下清單方塊中的其中一個專案。

     [**屬性**] 視窗會顯示專案的兩個屬性。

8. 變更其中一個屬性，然後按**enter**。

     專案會在 ListBox 中更新。
