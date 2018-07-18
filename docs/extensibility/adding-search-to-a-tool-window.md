---
title: 加入搜尋工具視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f3b5aa52968be5a2efcf88d7a31505d94f97aaec
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032066"
---
# <a name="adding-search-to-a-tool-window"></a>加入工具視窗搜尋
當您建立或更新您的擴充功能中的工具視窗時，您可以在 Visual Studio 中加入相同出現的其他位置的搜尋功能。 這項功能包含下列功能：  
  
-   一定會位於工具列的自訂區域中 [搜尋] 方塊中。  
  
-   進度列指示器，重疊在本身的 [搜尋] 方塊。  
  
-   若要顯示的結果，只要您輸入每個字元 （即時搜尋），或選擇 Enter 鍵 （視搜尋） 之後，才能力。  
  
-   顯示的條款，您搜尋過 最新清單。  
  
-   篩選搜尋特定欄位或搜尋目標方面的功能。  
  
 依循這個逐步解說，您將學習如何執行下列工作：  
  
1.  建立 VSPackage 專案。  
  
2.  建立工具視窗，其中包含與唯讀文字方塊 UserControl。  
  
3.  加入工具視窗的 [搜尋] 方塊。  
  
4.  加入搜尋實作。  
  
5.  啟用立即搜尋和顯示進度列。  
  
6.  新增**大小寫須相符**選項。  
  
7.  新增**搜尋才甚至行**篩選器。  
  
## <a name="to-create-a-vsix-project"></a>建立 VSIX 專案  
  
1.  建立 VSIX 專案，名為`TestToolWindowSearch`與名為工具視窗**TestSearch**。 如果您需要執行此動作的說明，請參閱[建立工具視窗擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="to-create-a-tool-window"></a>建立工具視窗  
  
1.  在`TestToolWindowSearch`專案中，開啟 TestSearchControl.xaml 檔案。  
  
2.  取代現有`<StackPanel>`具有下列的區塊中，加入唯讀區塊<xref:System.Windows.Controls.TextBox>至<xref:System.Windows.Controls.UserControl>工具視窗中。  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  在 TestSearchControl.xaml.cs 檔案中，加入下列 using 陳述式：  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  移除`button1_Click()`方法。  
  
     在**TestSearchControl**類別中，加入下列程式碼。  
  
     這個程式碼加入公用<xref:System.Windows.Controls.TextBox>屬性名為**SearchResultsTextBox**和公用的字串屬性，名為**SearchContent**。 在建構函式，SearchResultsTextBox 設為 [文字] 方塊中，而且 SearchContent 初始化為新行字元分隔的一組字串。 文字方塊的內容也會初始化字串的集合。  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體隨即出現。  
  
6.  在功能表列上選擇 **檢視**，**其他視窗**， **TestSearch**。  
  
     工具視窗隨即出現，但不會顯示搜尋控制項。  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>將在搜尋方塊新增至 [工具] 視窗  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼加入`TestSearch`類別。 程式碼會覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性，使傳回的 get 存取子`true`。  
  
     若要啟用搜尋，您必須覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>屬性。 <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch>，並提供不會啟用搜尋功能的預設實作。  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
3.  在 Visual Studio 的實驗執行個體，開啟**TestSearch**。  
  
     在 [工具] 視窗頂端，搜尋都會出現一個控制項與**搜尋**浮水印和玻璃放大圖示。 不過，搜尋不適用於尚未因為未實作搜尋程序。  
  
## <a name="to-add-the-search-implementation"></a>若要加入搜尋  
 當您啟用搜尋上<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>，如先前的程序，在 [工具] 視窗建立搜尋主機。 此主機設定及管理搜尋處理序，一律在背景執行緒進行。 因為<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>類別管理向上搜尋主機以及設定建立的搜尋，您只需要建立搜尋工作，但提供的搜尋方法。 搜尋程序會在背景執行緒，而工具視窗控制項呼叫會發生於 UI 執行緒上。 因此，您必須使用<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>管理您在處理控制項的任何呼叫的方法。  
  
1.  在 TestSearch.cs 檔案中，加入下列`using`陳述式：  
  
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
  
2.  在`TestSearch`類別中，加入下列程式碼，執行下列動作：  
  
    -   覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>方法來建立搜尋工作。  
  
    -   覆寫<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>方法，以還原在文字方塊中的狀態。 當使用者取消搜尋工作和使用者的設定或取消設定選項或篩選時，會呼叫這個方法。 同時<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>UI 執行緒上呼叫。 因此，您不需要存取文字方塊中，藉由<xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A>方法。  
  
    -   建立名為類別`TestSearchTask`繼承自<xref:Microsoft.VisualStudio.Shell.VsSearchTask>，其提供的預設實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>。  
  
         在`TestSearchTask`，建構函式設定參考的工具視窗的私用欄位。 若要提供的搜尋方法，您覆寫<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>和<xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>方法。 <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A>方法是您用來實作搜尋程序。 此程序包括執行搜尋，顯示在文字方塊中，搜尋結果，並呼叫這個方法，以報告搜尋已完成的基底類別實作。  
  
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
  
3.  執行下列步驟來測試您搜尋的實作：  
  
    1.  重建專案，並開始偵錯。  
  
    2.  在 Visual Studio 的實驗執行個體，請再次開啟工具視窗、 [搜尋] 視窗中輸入搜尋文字和按下 ENTER。  
  
         正確的結果應該會出現。  
  
## <a name="to-customize-the-search-behavior"></a>若要自訂搜尋行為  
 藉由變更搜尋設定，您可以在搜尋控制項的顯示方式，並執行搜尋時如何進行各種變更。例如，您可以變更浮水印 （預設的文字出現在 [搜尋] 方塊中）、 最小值和最大寬度的搜尋控制項，以及是否要顯示進度列。 您也可以變更的點顯示 （在需求或立即搜尋） 開始的搜尋結果，以及是否要顯示的條款，您最近搜尋清單。 您可以找到完整的清單中的設定<xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>類別。  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼加入`TestSearch`類別。 此程式碼可讓您立即的搜尋，而不是隨搜尋 （表示在使用者不需要按 ENTER）。 程式碼會覆寫`ProvideSearchSettings`方法中的`TestSearch`類別，需要變更預設設定。  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  測試新設定重建方案，然後重新啟動偵錯工具。  
  
     搜尋結果會顯示每次您在 [搜尋] 方塊中輸入字元。  
  
3.  在`ProvideSearchSettings`方法，加入下列行，可顯示進度列。  
  
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
  
     顯示進度列，就必須報告進度。 若要報告進度，請取消註解中的下列程式碼`OnStartSearch`方法`TestSearchTask`類別：  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  若要慢速處理足夠的進度列是可見的取消註解中的下列一行`OnStartSearch`方法`TestSearchTask`類別：  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  測試新的設定，請重新建置方案，然後啟動偵錯。  
  
     進度列會出現在 [搜尋] 視窗 （當做搜尋文字方塊下方藍線） 每次您執行搜尋。  
  
## <a name="to-enable-users-to-refine-their-searches"></a>若要讓使用者以精簡搜尋結果  
 您可以允許使用者透過選項精簡其搜尋，例如**大小寫須相符**或**字拼寫須相符**。 選項可以是布林值，其中會顯示為核取方塊或出現為按鈕的命令。 本逐步解說，您將建立布林值的選項。  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼加入`TestSearch`類別。 程式碼會覆寫`SearchOptionsEnum`方法，可允許搜尋實作，以偵測提供的選項是開啟或關閉。 中的程式碼`SearchOptionsEnum`新增選項，以便以大小寫須相符<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions>列舉值。 大小寫須相符的選項也都可以提供為`MatchCaseOption`屬性。  
  
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
  
2.  在`TestSearchTask`類別，請取消註解下列行中`OnStartSearch`方法：  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  測試選項：  
  
    1.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
    2.  在 [工具] 視窗中，選擇 [文字] 方塊右邊的向下箭號。  
  
         **大小寫須相符**出現核取方塊。  
  
    3.  選取**大小寫須相符**核取方塊，然後再執行 某些搜尋。  
  
## <a name="to-add-a-search-filter"></a>若要加入的搜尋篩選器  
 您可以加入搜尋篩選器可讓使用者以精簡搜尋目標集。 比方說，您可以在其已修改它們最近的日期和其檔案名稱的副檔名篩選檔案總管 中的檔案。 在本逐步解說中，您將加入只偶數行的篩選。 當使用者選擇該篩選條件時，搜尋主機會將搜尋查詢您指定的字串。 您可以識別這些字串搜尋方法內，並據以篩選的搜尋目標。  
  
1.  在 TestSearch.cs 檔案中，加入下列程式碼加入`TestSearch`類別。 程式碼會實作`SearchFiltersEnum`加<xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>指定篩選搜尋結果，甚至行只會出現。  
  
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
  
     搜尋控制項顯示搜尋篩選器現在`Search even lines only`。 當使用者選擇篩選器，字串`lines:"even"`會出現在 [搜尋] 方塊。 其他搜尋條件可以出現在相同的時間，做為篩選條件。 搜尋字串之後篩選器，或兩者都可能會出現之前篩選。  
  
2.  在 TestSearch.cs 檔案中，加入下列方法來`TestSearchTask`類別，這是在`TestSearch`類別。 這些方法支援`OnStartSearch`方法，您將在下一個步驟中修改。  
  
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
  
3.  在`TestSearchTask`類別中，更新`OnStartSearch`方法取代下列程式碼。 這項變更會更新以支援篩選器的程式碼。  
  
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
  
4.  測試您的程式碼。  
  
5.  建置此專案並開始偵錯。 在 Visual Studio 的實驗執行個體，開啟 [工具] 視窗，然後選擇搜尋控制項上的向下箭號。  
  
     **大小寫須相符**核取方塊和**搜尋才甚至行**篩選，會出現。  
  
6.  選擇篩選器。  
  
     [搜尋] 方塊包含**行:"甚至"**，和會出現下列結果：  
  
     良好的 2  
  
     4 良好  
  
     6 goodbye  
  
7.  刪除`lines:"even"`從 [搜尋] 方塊中，選取**大小寫須相符**核取方塊，然後再輸入`g`[搜尋] 方塊中。  
  
     此時會出現下列結果：  
  
     1 到  
  
     良好的 2  
  
     5 goodbye  
  
8.  選擇 [搜尋] 方塊右邊的 X。  
  
     清除搜尋，並顯示原始的內容。 不過，**大小寫須相符**仍然選取核取方塊。