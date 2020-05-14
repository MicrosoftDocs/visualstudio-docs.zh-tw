---
title: 將搜尋新增到工具視窗 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740144"
---
# <a name="add-search-to-a-tool-window"></a>將搜尋新增到工具視窗
在擴充中建立或更新工具視窗時,可以添加 Visual Studio 中其他位置顯示的相同搜尋功能。 此功能包括以下功能:

- 始終位於工具列自定義區域中的搜索框。

- 覆蓋在搜尋框本身上的進度指示器。

- 一旦輸入每個字元(即時搜索)或僅在選擇**Enter**鍵(按需搜尋)後,才能夠顯示結果。

- 顯示您最近搜尋的術語的清單。

- 按特定欄位或搜索目標的各個方面篩選搜索的能力。

以本演練,您將學習如何執行以下任務:

1. 建立 VSPackage 專案。

2. 建立包含具有唯讀文字框的使用者控制項的工具視窗。

3. 向工具視窗添加搜尋框。

4. 添加搜索實現。

5. 啟用進度列的即時搜索和顯示。

6. 添加**匹配案例**選項。

7. 添加**僅搜索偶數行**篩選器。

## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案

1. 使用名為**TestSearch**`TestToolWindowSearch`的工具視窗創建名為的 VSIX 專案。 如果需要協助執行此操作,請參考[使用工具視窗建立延伸](../extensibility/creating-an-extension-with-a-tool-window.md)。

## <a name="to-create-a-tool-window"></a>建立工具視窗

1. 在項目中`TestToolWindowSearch`,打開*TestSearchControl.xaml*檔案。

2. 將現有`<StackPanel>`塊替換為以下塊,該塊向工具視窗中的<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.UserControl>塊 添加唯讀。

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. 在*TestSearchControl.xaml.cs*檔案中,新增以下使用指令:

    ```csharp
    using System.Text;
    ```

4. 刪除`button1_Click()`方法。

     在**測試搜尋控制**類中,添加以下代碼。

     此代碼新增了名為<xref:System.Windows.Controls.TextBox>**「搜尋結果文字Box」** 的公共屬性和名為 **「搜尋內容」** 的公共字串屬性。 在建構函數中,Search結果文本Box設置為文本框,並且SearchContent被初始化為一組新行分隔的字串。 文字框的內容也會初始化為字串集。

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. 建置此專案並開始偵錯。 視覺工作室的實驗實例出現。

6. 在功能表列上,選擇 **「查看** > **其他 Windows** > **測試搜尋**」。

     將顯示工具視窗,但尚未顯示搜尋控制項。

## <a name="to-add-a-search-box-to-the-tool-window"></a>加入工具視窗

1. 在*TestSearch.cs*檔中,將以下代碼添加`TestSearch`到類。 程式碼重寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性 ,以便 get`true`存取器傳回 。

     要啟用搜索,必須重寫該<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性。 類<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>並提供不啟用搜索的默認實現。

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. 建置此專案並開始偵錯。 出現實驗實例。

3. 在視覺化工作室的實驗實例中,打開**測試搜尋**。

     在工具視窗的頂部,將顯示一個搜索控件,其中帶有**搜索**水印和放大鏡圖示。 但是,搜索尚未工作,因為搜索過程尚未實現。

## <a name="to-add-the-search-implementation"></a>新增搜尋實作
 在啟用 上<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>搜索 時,如上一過程所述,工具視窗將創建搜索主機。 此主機設置和管理搜索進程,這些進程始終發生在後台線程上。 由於<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類管理搜索主機的創建和搜索的設置,因此只需創建搜索任務並提供搜索方法。 搜索過程發生在後台線程上,對工具視窗控件的調用發生在UI線程上。 因此,您必須使用[ThreadHelper.Invoke®](https://msdn.microsoft.com/data/ee197798(v=vs.85))方法來管理在處理控制項時進行的任何調用。

1. TestSearch.cs*檔案*中,新增以下`using`指令:

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

2. 在類別`TestSearch`中,加入以下代碼,該代碼執行以下操作:

    - 重寫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>以建立搜索任務。

    - 重寫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>以還原文本框的狀態。 當使用者取消搜尋任務以及用戶設置或取消設置選項或篩選器時,將調用此方法。 和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>都調用 UI 線程。 因此,您無需通過[ThreadHelper.Invoke®](https://msdn.microsoft.com/data/ee197798(v=vs.85))方法訪問文本框。

    - 創建名為`TestSearchTask`從<xref:Microsoft.VisualStudio.Shell.VsSearchTask>繼承的類,該類提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>的 默認實現。

         在`TestSearchTask`中,建構函數設置引用工具視窗的專用欄位。 要提供搜索方法,請重寫和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A><xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。 該方法<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>是實現搜索過程的位置。 此過程包括執行搜索、在文本框中顯示搜尋結果以及調用此方法的基類實現以報告搜索已完成。

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

3. 通過執行以下步驟測試搜尋實現:

    1. 重建專案並開始調試。

    2. 在 Visual Studio 的實驗實體中,再次開啟工具視窗,在搜尋視窗中輸入一些搜尋文字,然後按**下 ENTER**。

         應顯示正確的結果。

## <a name="to-customize-the-search-behavior"></a>自訂搜尋行為
 通過更改搜尋設置,可以對搜索控制項的顯示方式和搜尋執行方式進行各種更改。例如,您可以更改浮浮水印(搜尋框中顯示的預設文本)、搜尋控制項的最小寬度和最大寬度,以及是否顯示進度條。 您還可以更改搜尋結果開始顯示的點(按需搜尋或即時搜索),以及是否顯示最近搜索的字詞清單。 您可以在<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>類別中找到完整的設定清單。

1. 在* TestSearch.cs* 檔案中,將以下代碼`TestSearch`添加到 類。 此代碼支援即時搜索,而不是按需搜索(這意味著使用者不必單擊**ENTER**)。 代碼重寫`ProvideSearchSettings``TestSearch`類中的方法,這是更改預設設置所必需的。

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. 通過重建解決方案並重新啟動調試器來測試新設置。

     每次在搜索框中輸入字元時,都會顯示搜尋結果。

3. 在`ProvideSearchSettings`方法中,添加以下行,從而顯示進度條。

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

     要顯示進度條,必須報告進度。 要報告進度,請取消註釋`OnStartSearch``TestSearchTask`類別方法中的以下代碼:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. 要使處理速度足夠慢,使進度條可見,請取消註釋`OnStartSearch``TestSearchTask`類方法中的以下行:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. 通過重建解決方案並開始調試來測試新設置。

     每次執行搜索時,進度列都會顯示在搜索視窗中(作為搜索文本框下方的藍線)。

## <a name="to-enable-users-to-refine-their-searches"></a>使用使用者能夠優化搜尋
 您可以允許使用者透過匹配**大小寫**或 **「匹配整個單詞**」等選項來優化其搜尋。 選項可以是布爾,顯示為複選框,也可以顯示為按鈕的命令。 在本演練中,您將創建一個布爾選項。

1. 在*TestSearch.cs*檔中,將以下代碼添加`TestSearch`到類。 代碼重寫該方法`SearchOptionsEnum`,該方法允許搜索實現檢測給定選項是打開還是關閉。 中`SearchOptionsEnum`的代碼添加一個選項,用於將大小寫匹配<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>到枚舉器。 匹配大小寫的選項也作為`MatchCaseOption`屬性提供。

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

2. 在類`TestSearchTask`中,取消註`OnStartSearch`釋 方法中的以下行:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. 測試選項:

    1. 建置此專案並開始偵錯。 出現實驗實例。

    2. 在工具視窗中,選擇文字框右側的向下箭頭。

         將顯示 **「匹配」案例**複選框。

    3. 選擇 **「匹配」案例**複選框,然後執行一些搜索。

## <a name="to-add-a-search-filter"></a>新增搜尋篩選器
 您可以添加允許使用者優化搜尋目標集的搜尋篩選器。 例如,您可以按檔案資源管理器中的檔最近修改的日期及其檔名副檔名篩選檔。 在本演練中,您將只為偶數行添加篩選器。 當使用者選擇該篩選器時,搜索主機會將指定的字串添加到搜索查詢中。 然後,您可以在搜索方法中標識這些字串,並相應地篩選搜索目標。

1. 在*TestSearch.cs*檔中,將以下代碼添加`TestSearch`到類。 代碼通過添加`SearchFiltersEnum`<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>指定來篩選搜尋結果,以便只顯示偶數行來實現。

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

     現在搜尋控制器顯示搜尋篩選器`Search even lines only`。 當使用者選擇篩選器時,字串`lines:"even"`將顯示在搜尋框中。 其他搜索條件可以與篩選器同時顯示。 搜索字串可能出現在篩選器之前、篩選器之後或兩者。

2. 在*TestSearch.cs*檔中,將以下方法添加到`TestSearchTask`類中 ,該類位於`TestSearch`類中。 這些方法支援該方法`OnStartSearch`,您將在下一步中修改該方法。

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

3. 在`TestSearchTask`類中,`OnStartSearch`使用以下代碼更新方法。 此更改更新代碼以支援篩選器。

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

4. 測試代碼。

5. 建置此專案並開始偵錯。 在 Visual Studio 的實驗實例中,打開工具視窗,然後選擇搜尋控制項上的向下箭頭。

     「**符合」的案例**複選方塊和 **「搜尋偶數行」僅**顯示篩選器。

6. 選擇篩選器。

     搜尋框包含**行:「偶數」** 並顯示以下結果:

     2 好

     4

     6 再見

7. 從`lines:"even"`搜尋框中移除,選擇 **「 符合」 的案例**, 然後在搜尋框`g`中輸入 。

     顯示以下結果:

     1 次

     2 好

     5 再見

8. 選擇搜尋框右側的 X。

     清除搜索,並顯示原始內容。 但是,"**匹配"案例**複選框仍被選中。
