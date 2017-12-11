---
title: "分析通用 Windows App 中的 CPU 使用量 | Microsoft Docs"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 59669f0430760bb98dd0cb63e05f433cb3a1fe54
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="analyze-cpu-usage-in-a-universal-windows-app-uwp"></a>分析通用 Windows App (UWP) 中的 CPU 使用量
![適用於 Windows 和 Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 當您需要調查應用程式的效能問題時，了解應用程式如何使用 CPU 是不錯的起點。 [CPU 使用量]  工具顯示 CPU 花時間執行程式碼的地方。 若要聚焦於特定情況，在單一診斷工作階段中，CPU 使用率可以與[應用程式時間軸](../profiling/application-timeline.md)工具和 (或) [能源消耗](../profiling/analyze-energy-use-in-store-apps.md)工具搭配執行。  
  
> [!NOTE]
>  **CPU 使用量**工具不得與 Windows Phone Silverlight 8.1 應用程式搭配使用。  
  
 此逐步解說會帶領您收集和分析簡單 Windows 通用 XAML app 的 CPU 使用量。  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a>建立 CpuUseDemo 專案  
 **CpuUseDemo** 是專為示範如何收集和分析 CPU 使用量資料所建立的應用程式。 這些按鈕會呼叫可從函式的多次呼叫中選取最大值的方法，來產生數字。 呼叫的函式會建立極大量的隨機值，然後傳回最後一個隨機值。 資料會以文字方塊的形式顯示。  
  
1.  使用 **BlankApp** 範本，建立名稱為 **CpuUseDemo** 的新 C# Windows 通用 app 專案。  
  
     ![建立 CpuUseDemoProject](../profiling/media/cpu_use_newproject.png "CPU_USE_NewProject")  
  
2.  以[此程式碼](#BKMK_MainPage_xaml)取代 MainPage.xaml。  
  
3.  以[此程式碼](#BKMK_MainPage_xaml_cs)取代 MainPage.xaml.cs。  
  
4.  建置並試用應用程式。這是簡單的應用程式，足以顯示 CPU 使用量資料分析的一些常見情況。  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> 收集 CPU 使用量資料  
 ![在模擬器中執行應用程式的發行組建](../profiling/media/cpu_use_wt_setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1.  在 Visual Studio 中，將部署目標設定為 [Simulator (模擬器)]，並將方案組態設定為 [Release (發行)]。  
  
    -   在模擬器中執行應用程式，可讓您輕鬆地切換應用程式與 Visual Studio IDE。  
  
    -   在 [Release (發行)] 模式中執行此應用程式，可讓您更適當地檢視應用程式的實際效能。  
  
2.  在 [偵錯]  功能表上選擇 [效能分析工具...] 。  
  
3.  在效能與診斷中樞中，選擇 [CPU Usage (CPU 使用量)]，然後選擇 [Start (開始)]。  
  
     ![開始 CpuUsage 診斷工作階段](../profiling/media/cpu_use_wt_perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4.  當應用程式啟動時，按一下 [取得最大數目] 。 在顯示輸出之後等候約 1 秒，然後選擇 [取得最大數目非同步] 。 在按鈕點選之間等候，可讓您更輕鬆地隔離診斷報告中的按鈕點選常式。  
  
5.  第二個輸出行出現之後，請選擇效能和診斷中樞中的 [停止收集]  。  
  
 ![停止 CpuUsage 資料收集](../profiling/media/cpu_use_wt_stopcollection.png "CPU_USE_WT_StopCollection")  
  
 CPU 使用量工具會分析資料，以及顯示報告。  
  
 ![CpuUsage 報表](../profiling/media/cpu_use_wt_report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a>分析 CPU 使用量報告  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a>CPU 使用率時間軸圖形  
 ![CPU 使用率 &#40;%&#41; 時間軸圖形](../profiling/media/cpu_use_wt_timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 CPU 使用率圖形顯示應用程式的 CPU 活動 (以裝置上所有處理器核心之所有 CPU 時間的百分比表示)。 這份報告的資料收集自雙核心電腦。 兩個大型高峰代表兩個按鈕按一下的 CPU 活動。 `GetMaxNumberButton_Click` 在單一核心上同步執行，因此方法的圖形高度絕不會超出 50%。 `GetMaxNumberAsycButton_Click` 跨兩個核心非同步執行，讓其高峰更接近以使用兩個核心上的所有 CPU 資源。  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a>選取時間軸區段以檢視詳細資料  
 使用 [Diagnostic session (診斷工作階段)] 時間軸上的選取列，聚焦於 GetMaxNumberButton_Click 資料：  
  
 ![已選取 GetMaxNumberButton&#95;Click](../profiling/media/cpu_use_wt_getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 [Diagnostic session (診斷工作階段)] 時間軸現在會顯示花在所選取區段的時間 (在此報告中，略高於 2 秒)，並篩選已在選取項目中執行之方法的呼叫樹狀圖。  
  
 現在，選取 `GetMaxNumberAsyncButton_Click` 區段。  
  
 ![GetMaxNumberAsyncButton&#95;Click 報告選取項目](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 此方法完成的速度大約比 `GetMaxNumberButton_Click` 快 1 秒，但是呼叫樹狀圖項目的意義較不明顯。  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀圖  
 若要開始了解呼叫樹狀圖資訊，請重新選取 `GetMaxNumberButton_Click` 區段，然後查看呼叫樹狀圖詳細資料。  
  
####  <a name="BKMK_Call_tree_structure"></a> 呼叫樹狀圖結構  
 ![GetMaxNumberButton&#95;Click 呼叫樹狀圖](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|CPU 使用量呼叫樹狀圖中的最上層節點是虛擬節點|  
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|在大部分的應用程式中，停用 [顯示外部程式碼]  選項時，第二層節點是一個含有系統和 Framework 程式碼的 [外部程式碼]  節點，而系統和 Framework 程式碼會啟動和停止應用程式、繪製 UI、控制執行緒排程，以及提供應用程式的其他低階服務。|  
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|第二層節點的子系是第二層系統和 Framework 程式碼所呼叫或建立的使用者程式碼方法和非同步常式。|  
|![步驟 4](../profiling/media/procguid_4.png "ProcGuid_4")|某個方法的子節點只包含父系方法呼叫的資料。 停用 [顯示外部程式碼]  時，應用程式方法也可包含 [外部程式碼]  節點。|  
  
####  <a name="BKMK_External_Code"></a> 外部程式碼  
 外部程式碼包含在系統和架構元件中由您撰寫之程式碼所執行的函式。 外部程式碼包含啟動和停止應用程式、繪製 UI、控制執行緒，以及將其他低階服務提供給應用程式的函式。 在大多數情況下，您對外部程式碼並不感興趣，因此 [CPU 使用量] 呼叫樹狀結構會將使用者方法的外部函式，收集成一個 [外部程式碼] 節點。  
  
 當您想要檢視外部程式碼的呼叫路徑時，請從 [篩選檢視]  清單中選擇 [顯示外部程式碼]  ，然後選擇 [套用] 。  
  
 ![選擇 [篩選檢視]，然後選擇 [ 顯示外部程式碼]](../profiling/media/cpu_use_wt_filterview.png "CPU_USE_WT_FilterView")  
  
 請注意，許多外部程式碼呼叫鏈結都是深度巢狀的，因此 [函式名稱] 資料行的寬度可能會超出所有電腦監視器 (但不含最大的電腦監視器) 的顯示寬度。 發生此情況時，函式名稱會顯示為 […]：  
  
 ![呼叫樹狀圖中的巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 使用搜尋方塊尋找您所尋找的節點，然後使用水平捲軸檢視資料：  
  
 ![搜尋巢狀外部程式碼](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> 呼叫樹狀圖資料行  
  
|||  
|-|-|  
|**CPU 總計 (%)**|![總計 % 資料方程式](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> 在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所使用的應用程式 CPU 活動百分比。 請注意，這與 [CPU 使用率]  時間軸圖表不同，後者會將時間範圍內的應用程式活動總計與可用的 CPU 容量總計進行比較。|  
|**自我 CPU (%)**|![自我 % 方程式](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> 在選取的時間範圍內，函式的呼叫所使用的應用程式 CPU 活動百分比 (不包括該函式所呼叫的函式活動)。|  
|**CPU 總計 (毫秒)**|在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所花費的毫秒數。|  
|**自我 CPU (毫秒)**|在選取的時間範圍內，函式的呼叫和該函式所呼叫的函式所花費的毫秒數。|  
|**模組**|內含函式的模組名稱，或內含 [外部程式碼] 節點中的函式的模組數目。|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU 使用量呼叫樹狀圖中的非同步函式  
 當編譯器發現非同步方法時，它會建立隱藏的類別來控制方法的執行。 就概念而言，這個類別是包含編譯器所產生之函式清單的狀態機器，這些函式會以非同步方式呼叫原始方法的作業，以及正常運作所需的回呼、排程器和 Iterator。 父方法呼叫原始方法時，執行階段會從父系的執行內容中移除該方法，並在可控制應用程式執行的系統和 Framework 程式碼內容中執行隱藏類別的方法。 非同步方法通常 (但不一定永遠) 會在一個或多個不同的執行緒上執行。 這段程式碼會在 [CPU 使用量] 呼叫樹狀圖中，顯示為樹狀圖最上層節點正下方之 [外部程式碼]  節點的子系。  
  
 若要在範例中查看此情況，請重新選取時間軸中的 `GetMaxNumberAsyncButton_Click` 區段。  
  
 ![GetMaxNumberAsyncButton&#95;Click 報表選取項目](../profiling/media/cpu_use_wt_getmaxnumberasync_selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 [外部程式碼]  下的前兩個節點是狀態機器類別之編譯器產生的方法。 第三個節點是原始方法的呼叫。 展開產生的方法可顯示正在進行的作業。  
  
 ![展開的 GetMaxNumberAsyncButton&#95;Click 呼叫樹狀圖](../profiling/media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` 的功能很有限；它會管理工作值清單、計算結果的最大值，並顯示輸出。  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` 會顯示排程和啟動將呼叫包裝至 `GetNumberAsync`之 48 項工作所需的活動。  
  
-   `MainPage::<GetNumberAsync>b__b` 會顯示呼叫 `GetNumber` 之所有工作的活動。  
  
##  <a name="BKMK_Next_steps"></a> 後續步驟  
 CpuUseDemo 應用程式不是最出色的應用程式，但是您可以使用它試驗非同步作業以擴充其公用程式，以及效能和診斷中樞中的其他工具。  
  
-   請注意，`MainPage::<GetNumberAsync>b__b` 在 [外部程式碼] 中花費的時間多於執行 GetNumber 方法。 此時間大部分都是非同步作業的額外負荷。 請嘗試增加工作數目 (設定於 MainPage.xaml.cs 的 `NUM_TASKS` 常數中)，並減少 `GetNumber` 中的反覆項目數 (變更 `MIN_ITERATIONS` 值)。 執行收集案例，並比較 `MainPage::<GetNumberAsync>b__b`的 CPU 活動與原始 CPU 使用量診斷工作階段中的 CPU 活動。 嘗試減少工作並增加反覆項目。  
  
-   使用者通常不在意您應用程式的實際效能，而是在意察覺到的應用程式效能和回應性。 XAML UI 回應性工具顯示 UI 執行緒上影響察覺到回應性的活動詳細資料。  
  
     在診斷和效能中樞中建立新的工作階段，並加入 XAML UI 回應性工具和 CPU 使用量工具。 執行收集案例。 如果您閱讀到此，報告可能未告訴您任何尚未了解的內容，除了兩種方法的 [UI 執行緒使用率] 時間軸圖形差異十分驚人以外。 在複雜的實際應用程式中，合併使用這些工具會十分有用。  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
```xaml  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
```CSharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
## <a name="see-also"></a>另請參閱
 [Visual Studio 中的分析](../profiling/index.md)  
 [程式碼剖析功能導覽](../profiling/profiling-feature-tour.md)