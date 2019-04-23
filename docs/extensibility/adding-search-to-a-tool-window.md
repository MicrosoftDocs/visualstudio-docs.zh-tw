---
title: 將搜尋新增至 工具視窗 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3c996b8b97217deb130d8e11a68b7efae01ee05
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077585"
---
# <a name="add-search-to-a-tool-window"></a>將搜尋新增至 工具視窗
當您建立或更新您的延伸模組中的工具視窗時，您可以在 Visual Studio 中新增其他地方出現的相同搜尋功能。 這項功能包含下列功能：

- 一定會位於工具列的自訂區域中 [搜尋] 方塊中。

- [搜尋] 方塊本身會有進度列指示器。

- 顯示結果，只要您輸入每個字元 （即時搜尋），或您選擇之後，才能夠**Enter**金鑰 （視搜尋）。

- 顯示讓您搜尋過最新的詞彙清單。

- 篩選搜尋特定欄位或搜尋目標方面的功能。

依照本逐步解說中，您將了解如何執行下列工作：

1. 建立 VSPackage 專案。

2. 建立工具視窗，其中包含唯讀的文字方塊與 UserControl。

3. 在搜尋方塊加入 [工具] 視窗中。

4. 加入搜尋實作。

5. 啟用即時搜尋和顯示進度列。

6. 新增**大小寫須相符**選項。

7. 新增**搜尋僅偶數行**篩選器。

## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案

1. 建立 VSIX 專案，名為`TestToolWindowSearch`名為工具視窗**TestSearch**。 如果您需要執行此動作的說明，請參閱[工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="to-create-a-tool-window"></a>若要建立工具視窗

1. 在 `TestToolWindowSearch`專案中，開啟*TestSearchControl.xaml*檔案。

2. 取代現有`<StackPanel>`具有下列的區塊中，加入唯讀區塊<xref:System.Windows.Controls.TextBox>到<xref:System.Windows.Controls.UserControl>工具視窗中。

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. 在  *TestSearchControl.xaml.cs*檔案中，新增下列 using 陳述式：

    ```csharp
    using System.Text;
    ```

4. 移除`button1_Click()`方法。

     在  **TestSearchControl**類別中，新增下列程式碼。

     這個程式碼加入公用<xref:System.Windows.Controls.TextBox>名為屬性**SearchResultsTextBox**和 公用字串屬性名為**SearchContent**。 在建構函式，SearchResultsTextBox 設為 [文字] 方塊中，而且 SearchContent 初始化為一組新行字元分隔的字串。 文字方塊的內容也會初始化一組字串。

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. 建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。

6. 在功能表列上選擇 **檢視** > **其他 Windows** > **TestSearch**。

     工具視窗隨即出現，但不會顯示搜尋控制項。

## <a name="to-add-a-search-box-to-the-tool-window"></a>若要將搜尋方塊新增至 [工具] 視窗

1. 在  *TestSearch.cs*檔案中，新增下列程式碼`TestSearch`類別。 程式碼會覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性，使傳回的 get 存取子`true`。

     若要啟用搜尋，您必須覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>，並提供不會啟用搜尋的預設實作。

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 建置此專案並開始偵錯。 實驗執行個體隨即出現。

3. 在 Visual Studio 的實驗性執行個體，開啟**TestSearch**。

     在 [工具] 視窗頂端，搜尋控制項是顯示為**搜尋**浮水印和放大半透明效果的圖示。 不過，搜尋不運作，還因為未實作搜尋程序。

## <a name="to-add-the-search-implementation"></a>若要加入搜尋實作
 當您啟用搜尋上<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>，如先前程序中，在 [工具] 視窗會建立搜尋主機。 此主機設定及管理搜尋處理序，一律在背景執行緒進行。 因為<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別管理向上搜尋主機以及設定建立的搜尋，您只需要建立搜尋工作，但提供的搜尋方法。 搜尋程序，就會發生在背景執行緒，並在 UI 執行緒上發生的工具視窗控制項的呼叫。 因此，您必須使用<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法來管理您在處理控制項的任何呼叫。

1. 在  *TestSearch.cs*檔案中，新增下列`using`陳述式：

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

2. 在 `TestSearch`類別中，新增下列程式碼，執行下列動作：

    - 覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>方法用來建立搜尋工作。

    - 覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>方法，以還原 [] 文字方塊中的狀態。 使用者取消搜尋工作，以及當使用者設定或取消設定選項或篩選時，會呼叫這個方法。 兩者<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI 執行緒上呼叫。 因此，您不需要存取文字方塊中，藉由<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法。

    - 會建立名為類別`TestSearchTask`繼承自<xref:Microsoft.VisualStudio.Shell.VsSearchTask>，以提供的預設實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>。

         在  `TestSearchTask`，建構函式設定參考的工具視窗的私用欄位。 若要提供的搜尋方法，您覆寫<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法是您用來實作搜尋程序。 此程序包含執行搜尋、 在文字方塊中，顯示搜尋結果，並呼叫基底類別實作，這個方法來搜尋已完成的報表。

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

3. 測試您的搜尋實作由執行下列步驟：

    1. 重建專案並開始偵錯。

    2. 在 Visual Studio 的實驗性執行個體，開啟 [工具] 視窗一次，在 [搜尋] 視窗中，輸入部分搜尋文字，按一下**ENTER**。

         正確的結果應該會出現。

## <a name="to-customize-the-search-behavior"></a>若要自訂搜尋行為
 藉由變更 [搜尋] 設定，您可以進行各種變更搜尋控制項的顯示方式，和如何搜尋執行中。例如，您可以變更浮水印 （出現在搜尋方塊中的預設文字）、 最小和最大寬度的搜尋控制項，以及是否要顯示進度列。 您也可以變更的點開始 （隨選或即時搜尋） 上會顯示哪一個搜尋結果，以及是否要顯示的條款，您最近搜尋清單。 您可以找到完整的清單中的設定<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>類別。

1. 在 * TestSearch.cs* 檔案中，新增下列程式碼`TestSearch`類別。 此程式碼會啟用即時的搜尋，而不是隨搜尋 (使用者不需要按 的意義**ENTER**)。 程式碼會覆寫`ProvideSearchSettings`方法中的`TestSearch`類別，這是必要變更預設設定。

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 測試新設定重建方案，然後重新啟動偵錯工具。

     搜尋結果會顯示每次您在搜尋方塊中輸入字元。

3. 在 `ProvideSearchSettings`方法中，新增下列行，允許顯示進度列。

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

     若要顯示進度列，必須報告進度。 若要報告進度，請取消註解中的下列程式碼`OnStartSearch`方法的`TestSearchTask`類別：

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 若要緩慢處理足夠的進度列是可見的取消註解中的下行`OnStartSearch`方法的`TestSearchTask`類別：

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 測試新的設定，請重新建置方案，然後啟動偵錯。

     進度列會出現在 [搜尋] 視窗 （如 [搜尋] 方塊下方的藍線） 每次您執行搜尋。

## <a name="to-enable-users-to-refine-their-searches"></a>若要讓使用者修正他們的搜尋
 您可以讓使用者透過選項修正他們的搜尋，例如**大小寫須相符**或是**字拼寫須相符**。 選項可以是布林值，其中會顯示為核取方塊或顯示為按鈕的命令。 此逐步解說中，您將建立布林值的選項。

1. 在  *TestSearch.cs*檔案中，新增下列程式碼`TestSearch`類別。 程式碼會覆寫`SearchOptionsEnum`方法，可讓偵測指定的選項是開啟或關閉搜尋實作。 中的程式碼`SearchOptionsEnum`新增選項，以便以大小寫須相符<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列舉值。 大小寫須相符的選項也都可以提供為`MatchCaseOption`屬性。

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

2. 在 `TestSearchTask`類別，取消註解下列行中`OnStartSearch`方法：

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 測試選項：

    1. 建置此專案並開始偵錯。 實驗執行個體隨即出現。

    2. 在 [工具] 視窗中，選擇 [文字] 方塊右邊的向下箭號。

         **大小寫須相符**出現核取方塊。

    3. 選取 **大小寫須相符**核取方塊，，然後再執行一些搜尋。

## <a name="to-add-a-search-filter"></a>若要加入搜尋篩選
 您可以加入搜尋篩選可讓使用者以精簡搜尋的目標集。 比方說，您也可以藉由在其修改最新的日期，以及其檔案名稱副檔名篩選檔案總管 中的檔案。 在本逐步解說中，您將新增僅偶數行的篩選條件。 當使用者選擇該篩選條件時，則搜尋主機會將您指定的字串將搜尋查詢。 您可以識別這些字串搜尋方法內，並據以篩選的搜尋目標。

1. 在  *TestSearch.cs*檔案中，新增下列程式碼`TestSearch`類別。 程式碼會實作`SearchFiltersEnum`藉由新增<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>，指定要篩選搜尋結果，如此只有偶數的行就會顯示。

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

     現在搜尋控制項中顯示搜尋篩選`Search even lines only`。 當使用者選擇的篩選字串`lines:"even"`會出現在搜尋方塊中。 其他搜尋條件可以出現在此同時做為篩選條件。 搜尋字串可能會出現在 篩選器之前之後篩選器，或兩者。

2. 在  *TestSearch.cs*檔案中，新增下列方法來`TestSearchTask`類別，這是在`TestSearch`類別。 這些方法支援`OnStartSearch`方法中，您會在下一個步驟中修改。

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

3. 在 `TestSearchTask`類別中，更新`OnStartSearch`為下列程式碼的方法。 這項變更會更新以支援篩選條件的程式碼。

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

5. 建置此專案並開始偵錯。 在 Visual Studio 的實驗性執行個體，開啟 [工具] 視窗，然後選擇搜尋控制項上的向下箭號。

     **大小寫須相符** 核取方塊並**搜尋只有偶數的線條**篩選會出現。

6. 選擇的篩選條件。

     搜尋方塊中包含**幾行： 偶數 」**，並會出現下列結果：

     良好的 2

     4 良好

     6 goodbye

7. 刪除`lines:"even"`從 [搜尋] 方塊中，選取**大小寫須相符**核取方塊，然後再輸入`g`在搜尋方塊中。

     此時會出現下列結果：

     1 個 go

     良好的 2

     5 goodbye

8. 選擇 [搜尋] 方塊右邊的 X。

     清除搜尋，和原始的內容會出現。 不過，**大小寫須相符**仍然選取核取方塊。