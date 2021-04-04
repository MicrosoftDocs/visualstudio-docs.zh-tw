---
title: 將搜尋新增至工具視窗 |Microsoft Docs
description: 瞭解如何將搜尋功能（包括搜尋方塊、篩選和進度指標）新增至 Visual Studio 中的工具視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca1998b5ca3ad78b269c50244ddf51796c9e4005
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215522"
---
# <a name="add-search-to-a-tool-window"></a>將搜尋新增至工具視窗
當您建立或更新延伸模組中的工具視窗時，可以新增在 Visual Studio 的其他位置出現的相同搜尋功能。 這項功能包含下列功能：

- 一律位於工具列自訂區域的搜尋方塊。

- 在搜尋方塊本身上重迭的進度指示器。

- 當您輸入每個字元 (立即搜尋) ，或只有在選擇 **enter** 鍵 (依需求搜尋) 時，才能夠顯示結果。

- 此清單會顯示您最近搜尋過的詞彙。

- 依特定欄位或搜尋目標的各方面篩選搜尋的能力。

遵循本逐步解說，您將瞭解如何執行下列工作：

1. 建立 VSPackage 專案。

2. 使用唯讀文字方塊建立包含 UserControl 的工具視窗。

3. 將搜尋方塊新增至工具視窗。

4. 新增搜尋執行。

5. 啟用即時搜尋和顯示進度列。

6. 新增 **Match case** 選項。

7. 新增 [ **只搜尋偶數行** ] 篩選。

## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案

1. `TestToolWindowSearch`使用名為 **TestSearch** 的工具視窗，建立名為的 VSIX 專案。 如果您需要協助，請參閱 [使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)模組。

## <a name="to-create-a-tool-window"></a>建立工具視窗

1. 在 `TestToolWindowSearch` 專案中，開啟 *TestSearchControl .xaml* 檔案。

2. 將現有的 `<StackPanel>` 區塊取代為下列區塊，此區塊會將唯讀新增 <xref:System.Windows.Controls.TextBox> 至 <xref:System.Windows.Controls.UserControl> 工具視窗中的。

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. 在 *TestSearchControl* 檔案中，加入下列 using 指示詞：

    ```csharp
    using System.Text;
    ```

4. 移除 `button1_Click()` 方法。

     在 **TestSearchControl** 類別中，加入下列程式碼。

     此程式碼會新增 <xref:System.Windows.Controls.TextBox> 名為 **SearchResultsTextBox** 的公用屬性，以及名為 **SearchContent** 的公用字串屬性。 在此函式中，SearchResultsTextBox 會設定為文字方塊，而 SearchContent 會初始化為以行分隔的字串集合。 文字方塊的內容也會初始化為一組字串。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/toolwindowsearch/cs/mycontrol.xaml.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/toolwindowsearch/vb/mycontrol.xaml.vb" id="Snippet1":::

5. 建置此專案並開始偵錯。 Visual Studio 的實驗實例隨即出現。

6. 在功能表列上，選擇 [ **View**  >  **Other Windows**  >  **TestSearch**]。

     工具視窗隨即出現，但是搜尋控制項還不會出現。

## <a name="to-add-a-search-box-to-the-tool-window"></a>將搜尋方塊新增至工具視窗

1. 在 *TestSearch .cs* 檔案中，將下列程式碼加入至 `TestSearch` 類別。 程式碼會覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 屬性，讓 get 存取子傳回 `true` 。

     若要啟用搜尋，您必須覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> 屬性。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> 會執行，並提供不啟用搜尋的預設值。

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 建置此專案並開始偵錯。 實驗實例隨即出現。

3. 在 Visual Studio 的實驗實例中，開啟 **TestSearch**。

     在工具視窗的頂端，搜尋控制項隨即出現，並顯示 **搜尋** 浮水印和放大鏡圖示。 不過，因為搜尋程式尚未執行，所以搜尋仍無法運作。

## <a name="to-add-the-search-implementation"></a>若要加入搜尋執行
 當您在上啟用搜尋時（ <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 如同在先前的程式中），工具視窗會建立搜尋主控制項。 此主機會設定及管理搜尋程式，而這些搜尋程式一律會在背景執行緒上發生。 因為 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> 類別會管理搜尋主機的建立以及搜尋的設定，所以您只需要建立搜尋工作，並提供搜尋方法。 搜尋進程會在背景執行緒上發生，而工具視窗控制項的呼叫會在 UI 執行緒上發生。 因此，您必須使用 [ThreadHelper *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 方法來管理您在處理控制項時所進行的任何呼叫。

1. 在 *TestSearch .cs* 檔案中，加入下列指示詞 `using` ：

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

2. 在 `TestSearch` 類別中加入下列程式碼，它會執行下列動作：

    - 覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> 方法以建立搜尋工作。

    - 覆寫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 方法以還原文字方塊的狀態。 當使用者取消搜尋工作，以及當使用者設定或取消設定選項或篩選準則時，就會呼叫這個方法。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> 都是在 UI 執行緒上呼叫。 因此，您不需要透過 [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) 方法來存取此文字方塊。

    - 建立名為的類別，這個類別會 `TestSearchTask` 繼承自 <xref:Microsoft.VisualStudio.Shell.VsSearchTask> ，它會提供的預設實值 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask> 。

         在中 `TestSearchTask` ，此函式會設定參考工具視窗的私用欄位。 若要提供搜尋方法，您可以覆寫 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> 和 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> 方法。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法是您執行搜尋進程的位置。 此套裝程式括執行搜尋、在文字方塊中顯示搜尋結果，以及呼叫這個方法的基類執行來報告搜尋已完成。

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

3. 藉由執行下列步驟來測試您的搜尋執行：

    1. 重建專案並開始進行調試。

    2. 在 Visual Studio 的實驗實例中，再次開啟工具視窗，在搜尋視窗中輸入一些搜尋文字，然後按一下 **Enter 鍵**。

         應該會顯示正確的結果。

## <a name="to-customize-the-search-behavior"></a>自訂搜尋行為
 藉由變更搜尋設定，您可以在搜尋控制項的顯示方式以及搜尋的執行方式方面進行各種變更。例如，您可以變更浮水印 (出現在搜尋方塊中的預設文字) 、搜尋控制項的最小和最大寬度，以及是否顯示進度列。 您也可以變更搜尋結果開始 (視需要或立即搜尋) 出現的時間點，以及是否要顯示您最近搜尋的字詞清單。 您可以在類別中找到完整的設定清單 <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> 。

1. 在 * TestSearch .cs * 檔案中，將下列程式碼加入至 `TestSearch` 類別。 這段程式碼會啟用立即搜尋，而不是依需求搜尋 (這表示使用者不需要按 **ENTER**) 。 程式碼會覆寫 `ProvideSearchSettings` 類別中的方法 `TestSearch` ，這是變更預設設定的必要方法。

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 藉由重建方案並重新啟動偵錯工具，來測試新的設定。

     每次在 [搜尋] 方塊中輸入字元時，就會出現搜尋結果。

3. 在 `ProvideSearchSettings` 方法中，加入下列程式程式碼，以便顯示進度列。

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

     若要顯示進度列，必須報告進度。 若要報告進度，請在類別的方法中取消批註下列程式碼 `OnStartSearch` `TestSearchTask` ：

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 若要讓處理速度變得很慢，可以看到進度列，請在類別的方法中取消批註下列程式 `OnStartSearch` `TestSearchTask` 程式碼：

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 藉由重建方案並開始進行偵錯工具，來測試新的設定。

     當您每次執行搜尋時，[搜尋] 視窗中會顯示進度列 (為 [搜尋] 文字方塊下的藍色線) 。

## <a name="to-enable-users-to-refine-their-searches"></a>讓使用者精簡搜尋
 您可以允許使用者藉由比對 **案例** 或 **全字** 相符等選項來精簡搜尋。 選項可以是 [布林值]，其會顯示為核取方塊或命令，這會顯示為按鈕。 在這個逐步解說中，您將建立布林值選項。

1. 在 *TestSearch .cs* 檔案中，將下列程式碼加入至 `TestSearch` 類別。 程式碼會覆寫 `SearchOptionsEnum` 方法，以允許搜尋執行偵測指定的選項是開啟或關閉。 中的程式碼會 `SearchOptionsEnum` 將符合大小寫的選項加入至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> 列舉值。 符合大小寫的選項也可做為 `MatchCaseOption` 屬性。

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. 在 `TestSearchTask` 類別中，取消批註方法中的下列程式 `OnStartSearch` 程式碼：

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 測試選項：

    1. 建置此專案並開始偵錯。 實驗實例隨即出現。

    2. 在工具視窗中，選擇文字方塊右邊的向下箭號。

         [ **符合案例** ] 核取方塊隨即出現。

    3. 選取 [ **符合案例** ] 核取方塊，然後執行一些搜尋。

## <a name="to-add-a-search-filter"></a>新增搜尋篩選
 您可以新增搜尋篩選器，讓使用者能夠精簡搜尋目標的集合。 例如，您可以依最近修改過的日期和副檔名來篩選檔案總管中的檔案。 在這個逐步解說中，您將只新增偶數行的篩選。 當使用者選擇該篩選時，搜尋主機會將您指定的字串新增至搜尋查詢。 然後，您可以在搜尋方法內識別這些字串，並據以篩選搜尋目標。

1. 在 *TestSearch .cs* 檔案中，將下列程式碼加入至 `TestSearch` 類別。 程式碼 `SearchFiltersEnum` 會藉由加入 <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> ，以指定篩選搜尋結果，只顯示偶數行。

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     現在搜尋控制項會顯示搜尋篩選準則 `Search even lines only` 。 當使用者選擇篩選準則時，該字串 `lines:"even"` 會出現在 [搜尋] 方塊中。 其他搜尋條件可以與篩選同時出現。 搜尋字串可能會出現在篩選準則之前、篩選準則之後，或兩者。

2. 在 *TestSearch .cs* 檔案中，將下列方法加入至類別 `TestSearchTask` 中的類別 `TestSearch` 。 這些方法支援 `OnStartSearch` 您將在下一個步驟中修改的方法。

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. 在 `TestSearchTask` 類別中， `OnStartSearch` 使用下列程式碼更新方法。 這種變更會更新程式碼以支援篩選。

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

     [比對 **案例** ] 核取方塊和 [ **只搜尋偶數行** ] 篩選準則隨即出現。

6. 選擇篩選準則。

     [搜尋] 方塊包含 **行： [偶數]**，並顯示下列結果：

     2好

     4好

     6再見

7. 從搜尋方塊中刪除 `lines:"even"` ，選取 [ **符合案例** ] 核取方塊，然後 `g` 在 [搜尋] 方塊中輸入。

     會出現下列結果：

     1 go

     2好

     5再見

8. 選擇搜尋方塊右邊的 X。

     搜尋會被清除，而且會顯示原始內容。 但是，[比對 **案例** ] 核取方塊仍為已選取狀態。
