---
title: 延伸屬性、工作清單、輸出、選項視窗
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711628"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>擴充屬性、工作清單、輸出和選項視窗
您可以造訪視覺化工作室中的任何工具視窗。 本演練展示如何將有關工具視窗的資訊整合到新的 **「選項」** 頁和 **「屬性**」 頁上的新設定中,以及如何寫入**工作清單**和**輸出**視窗。

## <a name="prerequisites"></a>Prerequisites
 從 Visual Studio 2015 開始,您不會從下載中心安裝 Visual Studio SDK。 它作為可選功能包含在可視化工作室設置中。 以後還可以安裝 VS SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

## <a name="create-an-extension-with-a-tool-window"></a>使用工具視窗建立延伸

1. 使用 VSIX 範本建立名為**TodoList**的專案,並添加名為**TodoWindow**的自定義工具視窗項範本。

    > [!NOTE]
    > 有關使用工具視窗建立擴充的詳細資訊,請參考[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="set-up-the-tool-window"></a>設定工具視窗
 添加用於鍵入新 ToDo 項的 TextBox、將新專案添加到清單中的按鈕以及用於顯示清單中專案的清單清單。

1. 在*TodoWindow.xaml*中 ,從使用者控制項中刪除按鈕、文字框和堆疊面板控制元件。

    > [!NOTE]
    > 這不會刪除**button1_Click**事件處理程式,您將在後面的步驟中重用該處理程式。

2. 從**工具箱****的所有 WPF 控制件**部分,將 **「畫布」** 控制器拖曳到網格。

3. 將**文字框**、**按鈕**和**列表框**拖動到畫布。 排列元素,使 TextBox 和按鈕位於同一級別,ListBox 將填充其下方的視窗的其餘部分,如下圖所示。

     ![完成的工具視窗](../extensibility/media/t5-toolwindow.png "T5 工具視窗")

4. 在 XAML 窗格中,找到「按鈕」並將其內容屬性設置為 **「添加**」 。 以新增`Click="button1_Click"`屬性將按鈕事件處理程式重新連接到 Button 控制件。 "畫布"塊應如下所示:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>自訂建構函數

1. 在*TodoWindowControl.xaml.cs*檔案中,新增以下使用指令:

    ```csharp
    using System;
    ```

2. 添加對 TodoWindow 的公共引用,並讓 TodoWindow 控制構造函數採用 TodoWindow 參數。 代碼應如下所示:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. 在*TodoWindow.cs*中,更改 TodoWindow 控制構造函數以包括 TodoWindow 參數。 代碼應如下所示:

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
 您可以在「**選項」** 對話方塊中提供頁面,以便使用者可以更改工具視窗的設定。 建立選項頁需要描述選項的類和*TodoListPackage.cs*或*TodoListPackage.vb*檔中的項目。

1. 新增名為 `ToolsOptions.cs`的類別。 使`ToolsOptions`類<xref:Microsoft.VisualStudio.Shell.DialogPage>從 繼承。

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. 加入以下 using 指示詞：

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. 本演練中的「選項」頁僅提供一個名為「天超」的選項。 新增`ToolsOptions`名為 **「天前」** 的私有欄位和名為 **「天前」** 的屬性:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   現在,您必須使專案瞭解此選項頁。

### <a name="make-the-options-page-available-to-users"></a>讓選項頁可供使用者使用

1. 在*TodoWindowPackage.cs*<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>中`TodoWindowPackage`, 向 類別加入 a:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. ProvideOptionPage 建構函數的第一個參數是之前創建的`ToolsOptions`類的類型。 第二個參數"ToDo"是 **"選項"** 對話方塊中的類別名稱。 第三個參數「一般」是 **「選項**」對話框的子類別的名稱,其中「選項」頁將可用。 接下來的兩個參數是字串的資源指示;另一個參數是字串的資源指示。第一個是類別的名稱,第二個是子類別的名稱。 最終參數確定是否可以使用自動化訪問此頁面。

     當使用者打開"選項"頁時,它應類似於下圖。

     ![選項頁面](../extensibility/media/t5optionspage.gif "T5選項頁")

     請注意 **「DoDo」** 類別和子類別 **「 一般**」。

## <a name="make-data-available-to-the-properties-window"></a>使資料可用於屬性視窗
 您可以通過創建名為"ToDo"`TodoItem`清單中儲存有關各個項的資訊的類,使 ToDo 清單資訊可用。

1. 新增名為 `TodoItem.cs`的類別。

     當使用者可以使用工具視窗時,ListBox 中的專案將由 TodoItems 表示。 當使用者在 ListBox 中選擇這些專案之一時,「**屬性」** 視窗將顯示有關該專案的資訊。

     要讓資料在 **「屬性」** 視窗中可用,請將資料轉換為具有兩個特殊屬性的公共`Description``Category`屬性和 。 `Description`是顯示在 **「屬性」** 視窗底部的文字。 `Category`確定**屬性**在 **「分類」** 檢視中顯示時應顯示的位置。 在下圖中,「**屬性」** 視窗位於 **「分類」** 檢視中,選擇了**ToDo 欄位**類別中**的「名稱**」屬性,並且 **「名稱」** 屬性的說明顯示在視窗底部。

     ![屬性視窗](../extensibility/media/t5properties.png "T5 屬性")

2. 使用*TodoItem.cs*檔案新增以下指令。

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. 將`public`訪問修改器添加到類聲明。

    ```csharp
    public class TodoItem
    {
    }
    ```

     新增兩個屬性`Name`與`DueDate`。 我們稍後再做`UpdateList()``CheckForErrors()`。

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

4. 向使用者控制件添加私有引用。 添加一個構造函數,該構造函數獲取此 ToDo 項的使用者控制項和名稱。 要尋找的值`daysAhead`,它取得「選項」頁屬性。

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

5. 由於類的`TodoItem`實例將存儲在 ListBox 中,ListBox`ToString`將調用 該函數`ToString`,因此必須重載 函數。 在建構函數之後和類結束之前將以下代碼添加到*TodoItem.cs*。。

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. 在*TodoWindowControl.xaml.cs*中,將`TodoWindowControl`存根`CheckForError`方法`UpdateList`添加到 和 方法的類中。 將它們放在進程對話查爾之後和文件結束之前。

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     該方法`CheckForError`將調用父物件中具有相同名稱的方法,該方法將檢查是否發生了任何錯誤並正確處理它們。 該方法`UpdateList`將更新父控件中的 ListBox;當類中的`Name`和`DueDate`屬性發生更改時,將調用 方法。 稍後將實施。

## <a name="integrate-into-the-properties-window"></a>整合到屬性視窗
 現在編寫管理 ListBox 的代碼,該代碼將綁定到 **「屬性」** 視窗。

 您必須更改按鈕按一下處理程式才能讀取文字框、創建 TodoItem 並將其添加到 ListBox。

1. 將現有`button1_Click`函數替換為創建新 TodoItem 並將其添加到 ListBox 的代碼。 它調用`TrackSelection()`,稍後將定義。

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

2. 在「設計」檢視中選擇「列表框」 控制件。 在「**屬性」** 視窗中按下 **「事件處理程式」** 按鈕,然後查找 **「選擇更改」** 事件。 用**listBox_SelectionChanged**填寫文字框。 執行此操作會為選擇更改處理程式添加一個存根,並將其分配給事件。

3. 實作 `TrackSelection()` 方法。 由於您需要獲取<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell><xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服務,因此需要通過 TodoWindowControl<xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>進行訪問。 將下列方法新增至 `TodoWindow` 類別：

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. 將以下使用指令加入*TodoWindowControl.xaml.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. 填寫「選擇更改」處理程式,如下所示:

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. 現在,填寫"軌道選擇"功能,該函數將提供與 **"屬性"** 視窗的集成。 當使用者將專案添加到 ListBox 或按一下 ListBox 中的專案時,將調用此功能。 它將 ListBox 的內容添加到選擇容器,並將選擇容器**Properties**傳遞到<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>屬性視窗的事件處理程式。 「軌跡選擇」服務追蹤使用者介面 (UI) 中的選擇物件並顯示其屬性

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

     現在,您擁有了 **「屬性」** 視窗可以使用的類,則可以將 **「屬性」** 視窗與工具視窗整合。 當使用者單擊工具視窗中的 ListBox 中的專案時,「**屬性」** 視窗應相應地更新。 同樣,當使用者在「**屬性」** 視窗中更改 ToDo 項時,應更新關聯的項。

7. 現在,在*TodoWindowControl.xaml.cs*中添加 UpdateList 函數代碼的其餘部分。 它應該從 ListBox 中刪除並重新新增修改後的 TodoItem。

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. 測試代碼。 建置此專案並開始偵錯。 應出現實驗實例。

9. 開啟 **'工具** > **選項"** 頁。 您應該在左側窗格中看到"ToDo"類別。 類別按字母順序出,因此請查看 Ts。

10. 在**Todo**選項頁上,應`DaysAhead`看到屬性 設定為**0**。 將改變為**2**。

11. 在 **'查看/ 其他視窗'** 選單上,開啟**TodoWindow**。 在文字框中鍵入**結束日期**,然後按下「**添加**」 。

12. 在清單框中,您應該比今天晚兩天看到日期。

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>將文字加入輸出輸出視窗,並將項目新增到工作清單
 在**工作清單**,您將建立類型 Task 的新物件,然後透過呼`Add`叫其 方法將該工作物件新增到**工作清單中**。 要寫入 **「輸出」** 視窗,請呼`GetPane`叫其 方法以獲取窗格物件,然後呼叫`OutputString`窗格物件 的方法。

1. 在*TodoWindowControl.xaml.cs*`button1_Click`中, 在 方法中添加代碼以獲取**輸出**視窗的 **「一般**」窗格(預設值),然後寫入它。 方法看起來應如下所示：

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

2. 要將項添加到工作清單,需要將嵌入套類添加到 TodoWindowControl 類。 巢狀類別需要派生自<xref:Microsoft.VisualStudio.Shell.TaskProvider>。 將以下代碼添加到類的`TodoWindowControl`末尾。

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

3. 接下來向`TodoTaskProvider``TodoWindowControl`類添加私有`CreateProvider()`引用和方法。 代碼應如下所示:

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

4. 添加`ClearError()`,這將清除任務清單,`ReportError()`並將 條目添加到任務`TodoWindowControl`清單, 到類。

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

5. 現在實現該方法`CheckForErrors`,如下所示。

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

1. 建置此專案並開始偵錯。 出現實驗實例。

2. 開啟**Todo 視窗**(**查看** > **其他視窗** > **todoWindow**).

3. 在文字框中鍵入內容,然後按下「**添加**」。

     今天之後的 2 天到期日期將添加到列表框中。 不產生錯誤,工作**清單**(**查看** > **工作清單**) 應沒有項目。

4. 現在將 **「工具** > **選項** > **ToDo」** 頁上的設定從**2**改為**0**。

5. 在**TodoWindow**中鍵入其他內容,然後按兩下"再次**添加**"。 這觸發了錯誤,並且還會在**工作清單中**輸入 。

     添加專案時,初始日期設置為現在加 2 天。

6. 在 **「查看」** 選單上,按下 **「輸出」** 以打開 **「輸出」** 視窗。

     請注意,每次添加專案時,工作**列表**窗格中都會顯示一條消息。

7. 按下清單框中的專案之一。

     **屬性「** 視窗顯示項目的兩個屬性」。

8. 變更其中一個屬性,然後按**Enter**。

     專案在清單框中更新。
