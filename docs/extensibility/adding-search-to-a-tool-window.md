---
title: 將搜尋新增至工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4414f6d907424a1abb56bccd1d1b125444e7c716
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648006"
---
# <a name="add-search-to-a-tool-window"></a>將搜尋新增至工具視窗
當您在擴充功能中建立或更新工具視窗時，可以加入 Visual Studio 中其他位置顯示的相同搜尋功能。 這項功能包括下列功能：

- 一律位於工具列之自訂區域中的搜尋方塊。

- 在搜尋方塊本身重迭的進度列指示器。

- 當您輸入每個字元（立即搜尋），或只在您選擇**enter**鍵（依需求搜尋）後，就能顯示結果。

- 此清單會顯示您最近搜尋過的詞彙。

- 依據特定欄位或搜尋目標的各個層面來篩選搜尋的功能。

藉由遵循此逐步解說，您將瞭解如何執行下列工作：

1. 建立 VSPackage 專案。

2. 建立工具視窗，其中包含具有唯讀文字方塊的 UserControl。

3. 將搜尋方塊新增至工具視窗。

4. 新增搜尋執行。

5. 啟用即時搜尋並顯示進度列。

6. 新增 [**符合案例**] 選項。

7. 新增 [**僅搜尋行**] 篩選準則。

## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案

1. 使用名為**TestSearch**的工具視窗，建立名為 `TestToolWindowSearch` 的 VSIX 專案。 如果您需要協助執行此作業，請參閱[使用工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)功能。

## <a name="to-create-a-tool-window"></a>建立工具視窗

1. 在 `TestToolWindowSearch` 專案中，開啟*TestSearchControl* 。

2. 以下列區塊取代現有的 `<StackPanel>` 區塊，這會將唯讀 <xref:System.Windows.Controls.TextBox> 新增至工具視窗中的 <xref:System.Windows.Controls.UserControl>。

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. 在*TestSearchControl.xaml.cs*檔案中，新增下列 using 指示詞：

    ```csharp
    using System.Text;
    ```

4. 移除 `button1_Click()` 方法。

     在**TestSearchControl**類別中，加入下列程式碼。

     此程式碼會新增名為**SearchResultsTextBox**的公用 <xref:System.Windows.Controls.TextBox> 屬性和名為**SearchContent**的公用字串屬性。 在此函式中，SearchResultsTextBox 會設定為文字方塊，而 SearchContent 會初始化為以分行符號分隔的字串組。 文字方塊的內容也會初始化成一組字串。

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. 建置此專案並開始偵錯。 Visual Studio 的實驗實例隨即出現。

6. 在功能表列上，選擇 [ **View**  > **其他 Windows**  > **TestSearch**]。

     工具視窗隨即出現，但搜尋控制項還不會出現。

## <a name="to-add-a-search-box-to-the-tool-window"></a>將搜尋方塊新增至工具視窗

1. 在*TestSearch.cs*檔案中，將下列程式碼新增至 `TestSearch` 類別。 程式碼會覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 屬性，讓 get 存取子傳回 `true`。

     若要啟用搜尋，您必須覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 屬性。 @No__t_0 類別會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>，並提供未啟用搜尋的預設實值。

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 建置此專案並開始偵錯。 實驗實例隨即出現。

3. 在 Visual Studio 的實驗實例中，開啟**TestSearch**。

     在工具視窗的頂端，搜尋控制項隨即出現，其中包含**搜尋**浮水印和放大鏡圖示。 不過，搜尋尚未執行，因為搜尋程式尚未完成。

## <a name="to-add-the-search-implementation"></a>若要加入搜尋執行
 當您在 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 上啟用搜尋時（如先前的程式所示），工具視窗會建立搜尋主機。 此主機會設定並管理搜尋程式，這一律會發生在背景執行緒上。 由於 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 類別會管理搜尋主機的建立和搜尋的設定，因此您只需要建立搜尋工作並提供搜尋方法。 搜尋程式會在背景執行緒上進行，而工具視窗控制項的呼叫會在 UI 執行緒上發生。 因此，您必須使用[ThreadHelper *](https://msdn.microsoft.com/data/ee197798(v=vs.85))方法來管理您在處理控制項時所進行的任何呼叫。

1. 在*TestSearch.cs*檔案中，新增下列 `using` 指示詞：

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Runtime.InteropServices;
    using System.Text;
    using System.Windows.Controls;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. 在 `TestSearch` 類別中，新增下列程式碼，以執行下列動作：

    - 覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 方法以建立搜尋工作。

    - 覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 方法以還原文字方塊的狀態。 當使用者取消搜尋工作，以及當使用者設定或取消設定選項或篩選時，會呼叫這個方法。 @No__t_0 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 都是在 UI 執行緒上呼叫。 因此，您不需要透過[ThreadHelper *](https://msdn.microsoft.com/data/ee197798(v=vs.85))方法來存取文字方塊。

    - 建立一個名為 `TestSearchTask` 的類別，它會繼承自 <xref:Microsoft.VisualStudio.Shell.VsSearchTask>，這會提供 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> 的預設執行。

         在 `TestSearchTask` 中，此函式會設定參考工具視窗的私用欄位。 若要提供搜尋方法，請覆寫 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 和 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> 方法。 @No__t_0 方法是您在其中執行搜尋程式的位置。 此套裝程式括執行搜尋、在文字方塊中顯示搜尋結果，以及呼叫此方法的基類實，以報告搜尋已完成。

    ```csharp
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)
    {
        if (pSearchQuery == null || pSearchCallback == null)
            return null;
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);
    }

    public override void ClearSearch()
    {
        TestSearchControl control = (TestSearchControl)this.Content;
        control.SearchResultsTextBox.Text = control.SearchContent;
    }

    internal class TestSearchTask : VsSearchTask
    {
        private TestSearch m_toolWindow;

        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)
            : base(dwCookie, pSearchQuery, pSearchCallback)
        {
            m_toolWindow = toolwindow;
        }

        protected override void OnStartSearch()
        {
            // Use the original content of the text box as the target of the search.
            var separator = new string[] { Environment.NewLine };
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);

            // Get the search option.
            bool matchCase = false;
            // matchCase = m_toolWindow.MatchCaseOption.Value;

                // Set variables that are used in the finally block.
                StringBuilder sb = new StringBuilder("");
                uint resultCount = 0;
                this.ErrorCode = VSConstants.S_OK;

                try
                {
                    string searchString = this.SearchQuery.SearchString;

                    // Determine the results.
                    uint progress = 0;
                    foreach (string line in contentArr)
                    {
                        if (matchCase == true)
                        {
                            if (line.Contains(searchString))
                            {
                                sb.AppendLine(line);
                                resultCount++;
                            }
                        }
                        else
                            {
                                if (line.ToLower().Contains(searchString.ToLower()))
                                {
                                    sb.AppendLine(line);
                                    resultCount++;
                                }
                            }

                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                            // Uncomment the following line to demonstrate the progress bar.
                            // System.Threading.Thread.Sleep(100);
                        }
                    }
                    catch (Exception e)
                    {
                        this.ErrorCode = VSConstants.E_FAIL;
                    }
                    finally
                    {
                        ThreadHelper.Generic.Invoke(() =>
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

                        this.SearchResults = resultCount;
                    }

            // Call the implementation of this method in the base class.
            // This sets the task status to complete and reports task completion.
            base.OnStartSearch();
        }

        protected override void OnStopSearch()
        {
            this.SearchResults = 0;
        }
    }
    ```

3. 執行下列步驟來測試您的搜尋執行：

    1. 重建專案並開始進行調試。

    2. 在 Visual Studio 的實驗實例中，再次開啟工具視窗，在 [搜尋] 視窗中輸入一些搜尋文字，然後按一下**Enter 鍵**。

         應該會出現正確的結果。

## <a name="to-customize-the-search-behavior"></a>自訂搜尋行為
 藉由變更搜尋設定，您可以在搜尋控制項的顯示方式以及搜尋的執行方式中，進行各種變更。例如，您可以變更浮水印（出現在 [搜尋] 方塊中的預設文字）、搜尋控制項的最小和最大寬度，以及是否要顯示進度列。 您也可以變更搜尋結果開始出現的點（視需要或立即搜尋），以及是否要顯示您最近搜尋過的字詞清單。 您可以在 <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> 類別中找到完整的設定清單。

1. 在 * TestSearch.cs * 檔案中，將下列程式碼新增至 `TestSearch` 類別。 這段程式碼會啟用立即搜尋，而不是點播搜尋（這表示使用者不需要按**ENTER**）。 程式碼會覆寫 `TestSearch` 類別中的 `ProvideSearchSettings` 方法，這是變更預設設定所需的。

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 藉由重建方案並重新啟動偵錯工具，來測試新的設定。

     每次您在 [搜尋] 方塊中輸入字元時，就會出現搜尋結果。

3. 在 `ProvideSearchSettings` 方法中，新增下列程式程式碼，以啟用進度列的顯示。

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);
    }
    ```

     若要顯示進度列，必須回報進度。 若要報告進度，請在 `TestSearchTask` 類別的 `OnStartSearch` 方法中取消批註下列程式碼：

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 若要讓處理常式變慢，使進度列可見，請在 `TestSearchTask` 類別的 `OnStartSearch` 方法中取消批註下列程式程式碼：

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 藉由重建方案並開始進行 debug，來測試新的設定。

     每次執行搜尋時，進度列都會出現在 [搜尋] 視窗中（作為 [搜尋] 文字方塊下方的藍色線）。

## <a name="to-enable-users-to-refine-their-searches"></a>讓使用者精簡其搜尋
 您可以讓使用者透過**符合大小寫**或**符合全字**組的選項來縮小搜尋範圍。 選項可以是布林值，它會顯示為核取方塊或命令，並顯示為按鈕。 在此逐步解說中，您將建立布林值選項。

1. 在*TestSearch.cs*檔案中，將下列程式碼新增至 `TestSearch` 類別。 程式碼會覆寫 `SearchOptionsEnum` 方法，讓搜尋執行能夠偵測指定的選項為開啟或關閉。 @No__t_0 中的程式碼會新增一個選項，以符合 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 列舉值的大小寫。 符合大小寫的選項也可當做 `MatchCaseOption` 屬性來使用。

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
    {
        get
        {
            if (m_optionsEnum == null)
            {
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();

                list.Add(this.MatchCaseOption);

                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;
            }
            return m_optionsEnum;
        }
    }

    private WindowSearchBooleanOption m_matchCaseOption;
    public WindowSearchBooleanOption MatchCaseOption
    {
        get
        {
            if (m_matchCaseOption == null)
            {
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);
            }
            return m_matchCaseOption;
        }
    }
    ```

2. 在 `TestSearchTask` 類別中，取消批註 `OnStartSearch` 方法中的下列程式程式碼：

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 測試選項：

    1. 建置此專案並開始偵錯。 實驗實例隨即出現。

    2. 在工具視窗中，選擇文字方塊右邊的向下箭號。

         [**符合案例**] 核取方塊隨即出現。

    3. 選取 [**符合案例**] 核取方塊，然後執行一些搜尋。

## <a name="to-add-a-search-filter"></a>新增搜尋篩選準則
 您可以新增搜尋篩選準則，讓使用者精簡搜尋目標的集合。 例如，您可以在 [檔案管理器] 中依最近修改的日期和其副檔名來篩選檔案。 在此逐步解說中，您將只新增偶數行的篩選。 當使用者選擇該篩選準則時，搜尋主機就會將您指定的字串新增至搜尋查詢。 接著，您可以在搜尋方法中識別這些字串，並據以篩選搜尋目標。

1. 在*TestSearch.cs*檔案中，將下列程式碼新增至 `TestSearch` 類別。 程式碼會藉由新增 <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> 來執行 `SearchFiltersEnum`，以篩選搜尋結果，只顯示偶數行。

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     現在搜尋控制項會顯示搜尋篩選 `Search even lines only`。 當使用者選擇篩選時，字串 `lines:"even"` 會出現在 [搜尋] 方塊中。 其他搜尋條件可以與篩選同時出現。 搜尋字串可能會出現在篩選準則之前、篩選後或兩者。

2. 在*TestSearch.cs*檔案中，將下列方法新增至 `TestSearch` 類別中的 `TestSearchTask` 類別。 這些方法支援 `OnStartSearch` 方法，您將在下一個步驟中加以修改。

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. 在 `TestSearchTask` 類別中，使用下列程式碼更新 `OnStartSearch` 方法。 這種變更會更新程式碼以支援篩選準則。

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);

        // Get the search option. 
        bool matchCase = false;
        matchCase = m_toolWindow.MatchCaseOption.Value;

        // Set variables that are used in the finally block.
        StringBuilder sb = new StringBuilder("");
        uint resultCount = 0;
        this.ErrorCode = VSConstants.S_OK;

        try
        {
            string searchString = this.SearchQuery.SearchString;

            // If the search string contains the filter string, filter the content array. 
            string filterString = "lines:\"even\"";

            if (this.SearchQuery.SearchString.Contains(filterString))
            {
                // Retain only the even items in the array.
                contentArr = GetEvenItems(contentArr);

                // Remove 'lines:"even"' from the search string.
                searchString = RemoveFromString(searchString, filterString);
            }

            // Determine the results. 
            uint progress = 0;
            foreach (string line in contentArr)
            {
                if (matchCase == true)
                {
                    if (line.Contains(searchString))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }
                else
                {
                    if (line.ToLower().Contains(searchString.ToLower()))
                    {
                        sb.AppendLine(line);
                        resultCount++;
                    }
                }

                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));

                // Uncomment the following line to demonstrate the progress bar. 
                // System.Threading.Thread.Sleep(100);
            }
        }
        catch (Exception e)
        {
            this.ErrorCode = VSConstants.E_FAIL;
        }
        finally
        {
            ThreadHelper.Generic.Invoke(() =>
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });

            this.SearchResults = resultCount;
        }

        // Call the implementation of this method in the base class. 
        // This sets the task status to complete and reports task completion. 
        base.OnStartSearch();
    }
    ```

4. 測試您的程式碼。

5. 建置此專案並開始偵錯。 在 Visual Studio 的實驗實例中，開啟工具視窗，然後選擇搜尋控制項上的向下箭號。

     [比對**案例**] 核取方塊和 [**僅搜尋行數**] 篩選準則隨即出現。

6. 選擇 [篩選]。

     [搜尋] 方塊包含**行：「偶數**」，並顯示下列結果：

     2良好

     4好

     6再見

7. 從 [搜尋] 方塊中刪除 `lines:"even"`，選取 [**相符案例**] 核取方塊，然後在 [搜尋] 方塊中輸入 `g`。

     會顯示下列結果：

     1 go

     2良好

     5再見

8. 選擇 [搜尋] 方塊右邊的 [X]。

     搜尋會清除，並顯示原始內容。 不過，仍然會選取 [**符合案例**] 核取方塊。
