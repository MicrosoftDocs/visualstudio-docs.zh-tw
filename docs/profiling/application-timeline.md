---
title: 分析 XAML 應用程式中的資源耗用量
description: 使用應用程式時間軸分析工具來尋找 XAML 應用程式中的效能問題。 您可以針對各種案例中的各種工作，分析花費的時間。
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 8fc482e10ae1ca08230feb38eb2997d0c4dcab00
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205732"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>分析資源耗用量和 UI 執行緒活動 (XAML)

使用 [應用程式時間軸]  程式碼剖析工具來找出並修正 XAML 應用程式中的應用程式互動相關效能問題。 此工具可透過顯示應用程式資源耗用量的詳細檢視，來協助改善 XAML 應用程式的效能。 您可以分析應用程式準備 UI 框架 (版面配置和轉譯)、服務網路和磁碟要求，以及像是應用程式啟動、頁面載入和視窗大小調整等情況所花費的時間。

[應用程式時間軸] 是可透過 [偵錯] > [效能分析工具] 命令啟動的工具之一。

此工具會取代 [XAML UI 回應性]  工具，而後者為 Visual Studio 2013 診斷工具組的一部分。

您可以在下列平台上使用此工具：

- 通用 Windows 應用程式 (於 Windows 10 上)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 (含) 以上版本)
- Windows 7

> [!NOTE]
> 除了 [時間軸]  資料之外，您還可以收集並分析 CPU 使用量資料和能源消耗資料。 請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

## <a name="collect-application-timeline-data"></a>收集應用程式時間軸資料

您可以在本機電腦、連接的裝置、Visual Studio 模擬器 (Simulator 或 Emulator) 或遠端裝置上分析應用程式的回應性。 請參閱 [使用或不使用偵錯工具來執行程式碼剖析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)。

> [!TIP]
> 請盡可能直接在裝置上執行應用程式。 在模擬器上或透過遠端桌面連接觀察到的應用程式效能，可能與裝置上的實際效能不同。 相反地，使用 Visual Studio 遠端工具收集資料並不會影響效能資料。

基礎步驟如下：

1. 開啟 XAML 應用程式。

2. 按一下 [ **Debug/效能分析工具**]。 您應該會在 .diagsession 視窗中看到一份程式碼剖析工具清單。

3. 選取 [應用程式時間軸]  ，然後在視窗底部按一下 [開始]  。

   ![已選取應用程式時間軸工具](../profiling/media/apptimelineselect.png "應用程式時間軸工具")

   > [!NOTE]
   > 您可能會看到 [使用者帳戶控制] 視窗要求您執行 *VsEtwCollector.exe* 的許可權。 按一下 [是]  。

4. 執行您感興趣用來在應用程式中程式碼剖析的案例，來收集效能資料。

5. 若要停止程式碼剖析，請切換回 .diagsession 視窗，並在視窗頂端按一下 [停止]  。

   Visual Studio 會分析收集到的資料並顯示結果。

   ![時間表分析工具報告](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>分析時間軸分析資料

收集到分析資料之後，您可以使用下面這些步驟開始分析：

1. 檢視 [UI 執行緒使用率] 和 [視覺輸送量 (FPS)] 圖形中的資訊，然後使用時間軸導覽列選取您要分析的時間範圍。

2. 使用 [UI 執行緒使用率] 或 [視覺輸送量 (FPS)] 圖形中的資訊，檢查 [時間軸詳細資料] 檢視中的詳細資料，找出任何明顯缺乏回應性的可能原因。

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a> 報表案例、類別和事件

[應用程式時間軸]  工具會顯示與 XAML 效能相關之情節、分類和事件的計時資料。

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a> 診斷工作階段時間軸

![效能及診斷時間軸](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

頁面頂端的尺規顯示所分析資訊的時間軸。 這個時間軸同時適用於 [ **UI 執行緒使用率** ] 圖形和 [ **視覺輸送量** ] 圖形。 您可以拖曳時間軸上的巡覽列，選取時間軸的區段，以縮小報告範圍。

時間軸也會顯示您已插入的所有使用者標記，以及應用程式的啟用週期事件。

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a> UI 執行緒使用率圖

![CPU 使用率圖形](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

[UI 執行緒使用率 (%)]  圖是顯示某項分類在收集時間範圍內相對花費之時間量的橫條圖。

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a> 視覺輸送量 (FPS) 圖

![視覺輸送量圖表](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

[ **視覺輸送量 (FPS)** ] 折線圖會顯示應用程式 UI 和撰寫執行緒上的每秒畫面格數 (FPS)。

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a> 時間軸詳細資料

詳細資料檢視是您會花費大部分時間來分析報表的所在。 會顯示由 UI 架構子系統分類的應用程式 CPU 使用率，或耗用 CPU 系統的元件。

支援的事件如下：

|名稱|描述|
|-|-|
|**剖析**|剖析 XAML 檔案和建立物件所花費的時間。<br /><br /> 展開 [時間軸詳細資料] 中的 [剖析] 節點，會顯示由於根事件而剖析的所有 XAML 檔案相依性鏈結。 這可讓您識別效能敏感情節中不必要的檔案剖析和物件建立作業，並排除這些作業以取得最佳化。|
|**版面配置**|在大型應用程式裡，螢幕上可能會同時顯示數千個項目。 此顯示可能導致低 UI 畫面播放速率和對應不佳的應用程式回應性。 配置事件準確地判斷每個項目的配置成本 (也就是在 Arrange、Measure、ApplyTemplate、ArrangeOverride 和 MeasureOverride 中所花的時間)。 也會建置參與版面配置階段的視覺化樹狀結構。 您可以使用此視覺效果，來判斷要清除哪些邏輯樹狀結構，或評估其他延遲機制以最佳化版面配置階段。|
|**轉譯**|將 XAML 項目繪製到螢幕所花費的時間。|
|**I/0**|從本機磁碟或網路資源 (透過 [Microsoft Windows 網際網路 (WinINet) API](/windows/desktop/WinInet/portal)存取) 擷取資料所花費的時間。|
|**應用程式程式碼**|執行與剖析或配置不相關應用程式 (使用者) 程式碼所花費的時間。|
|**XAML 其他**|執行 XAML 執行階段程式碼所花費的時間。|

> [!TIP]
> 當您開始進行程式碼剖析以檢視 UI 執行緒上所執行的應用程式時，請選擇 [CPU 使用量]  工具和 [應用程式時間軸]  工具。 將長時間執行的應用程式程式碼移到背景執行緒可以改善 UI 回應性。

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a> 自訂時間軸詳細資料

您可以使用 [時間軸詳細資料]  工具列來排序、篩選及指定 [時間軸詳細資料]  檢視項目的註釋。

|名稱|描述|
|-|-|
|**排序依據**|依開始時間或事件長度排序。|
|![依畫面格分組事件](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|加入或移除依框架分組事件的最上層 [框架]  分類。|
|![篩選時間軸詳細資料清單](../profiling/media/timeline_filter.png "TIMELINE_Filter")|依選取的分類和事件長度篩選清單。|
|![自訂時間軸詳細資料資訊](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|可讓您指定事件的註釋。|

## <a name="see-also"></a>請參閱

- [WPF team blog：適用于 WPF 應用程式的新 UI 效能分析工具](/archive/blogs/wpf/new-ui-performance-analysis-tool-for-wpf-applications)
- [使用 C++、C# 及 Visual Basic 的 UWP App 效能最佳做法](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [最佳化 WPF 應用程式效能](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)