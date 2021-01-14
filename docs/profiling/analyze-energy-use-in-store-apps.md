---
title: 分析 UWP App 中的能源耗用量 | Microsoft Docs
description: 使用 Visual Studio 能源消耗分析工具，分析在以電池供電的裝置上執行的 UWP 應用程式的能源和電源需求。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: cf55035ba5a05917334b2192067a3273f4930775
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205784"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>分析 UWP App 中的能源耗用量

Visual Studio [能源消耗] 分析工具可協助您分析 UWP App 在全部或部分時間使用自己的電池執行之低電源平板裝置上的功率和能源消耗情形。 在電池供電的裝置上，使用太多能源的應用程式可能導致客戶諸多不滿，最後客戶可能會解除安裝應用程式。 最佳化能源利用，可以提高客戶對應用程式的採用率。

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>能源消耗分析工具是什麼，它的運作方式為何，以及測量什麼內容

[能源消耗] 分析工具會在分析工作階段期間，擷取裝置的顯示器、CPU 和網路連線的活動。 然後它會產生這些活動的用電量評估，以及該分析工作階段的總計能源量。

> [!NOTE]
> 能源分析工具會使用代表可能執行應用程式的低電源平板裝置之標準參考裝置硬體的軟體模型，評估用電和能源利用。 為了提供最佳評估結果，建議您在低電源平板裝置上收集分析資料。
>
> 雖然這個模型可針對各種低電源裝置提供良好評估，但是您所分析裝置的實際值仍可能有所不同。 使用這些值找出相對於其他資源來說耗用量較高，也因此可能是合適的最佳化候選項目的顯示器、CPU 和網路活動。

[能源消耗] 分析工具使用下列「 *功率* 」(Power) 和「 *能源*」(Energy) 的定義：

- 「*功率* 」(Power) 用於測量在某段時間內完成工作的用電速率。 在電子學中，功率的標準單位是「 *瓦*」(Watt)，其定義為一安培電流流經一伏特電位差時，工作完成的速率。 在 [用電量]  圖形上，單位顯示為毫瓦 **mW** ，相當於千分之一瓦特。

   請注意，由於功率是一種速率，因此有方向 (工作在某段時間內可能增加或減少) 和速度 (工作增加或減少的量)。

- 「*能源* 」(Energy) 用於測量總功率，以容量或電位、電池的電量，或某段時間的累計總用電量表示。 能源的單位是瓦-小時，一小時內連續產生的一瓦功率數。 在 [ **能源摘要**] 中，單位顯示為毫瓦-小時 [ **mW-h**]。

![能源容量、耗電量、消耗的能源總計](../profiling/media/energyprof_capcitypowerused.png)

例如，平板電腦中完全充電的電池有特定的儲存電能量。 當能源用來執行像是網路通訊、計算值或顯示圖形這類工作時，電池的電力會以不同的速率消耗。 任一段時間內的總耗電量也是以能源測量。

## <a name="identify-scenarios-with-user-marks"></a>透過使用者標記識別情節
 您可以將「 *使用者標記* 」(User Mark) 加入至分析資料，以便識別時間軸尺規中的區段。

 ![時間軸中的使用者標記](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 在方法執行的時候，該標記會在時間軸中顯示為橙色三角形。 當您將游標停留在標記上時，訊息和時間就會做為工具提示顯示。 如果兩個以上的使用者標記很接近，標記會合併，並且工具提示資料會結合在一起。 您可以放大時間軸來分隔標記。

 **將標記加入至 C#、Visual Basic、C++ 程式碼**

 若要將使用者標記新增至 C#、Visual Basic、C++ 程式碼中，請先建立 <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> 物件。 接著，請在程式碼中您要標記的位置插入 <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> 方法的呼叫。 並在呼叫中使用 [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) 。

 當方法執行時，使用者標記就會與訊息一起加入至分析資料中。

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> 會實作 <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> 介面 (在 C# 和 VB 中投影為 <xref:System.IDisposable?displayProperty=nameWithType>)。 若要避免作業系統資源流失，請在完成記錄通道時呼叫 <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> (在 C# 和 VB 中呼叫 <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType>)。
> - 每個開啟的記錄通道都必須具有唯一名稱。 如果您嘗試使用與尚未處置的通道相同的名稱來建立新的記錄通道，則會擲回例外狀況。

如需範例程式碼，請參閱 Windows SDK 範例：[LoggingSession 範例](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) \(英文\)。

::: moniker range="vs-2017"
**將標記加入至 JavaScript 程式碼**

若要加入使用者標記，請在程式碼中您要標記的位置，插入下列程式碼：

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription* 這個字串包含要在使用者標記工具提示中顯示的訊息。
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>設定您的環境以進行分析
 為了獲得較佳的評估結果，建議您分析以本身電池供電之低電源裝置上的應用程式能源使用情形。 由於這類裝置大部分不會執行 Visual Studio，因此您需要將 Visual Studio 電腦連接到使用 Visual Studio 遠端工具的裝置。 若要連接到遠端裝置，您必須設定 Visual Studio 專案和遠端裝置。 如需詳細資訊，請參閱[在遠端電腦上執行 UWP App](../debugger/run-windows-store-apps-on-a-remote-machine.md)。

> [!TIP]
> - 我們不建議在 UWP 模擬器或 Visual Studio 電腦上進行能源分析。 在實際裝置上進行分析可提供更實際的資料。
> - 在以電池供電的目標裝置上進行分析。
> - 關閉其他可能使用相同資源 (網路、CPU 或顯示器) 的應用程式。

## <a name="collect-energy-profile-data-for-your-app"></a>收集應用程式的能源分析資料

1. 在 [偵錯]  功能表上，選擇 [啟動診斷但不偵錯] 。

     ![選擇效能分析工具中的能源耗用量](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. 選擇 [ **能源消耗** ]，然後選擇 [ **開始**]。

    > [!NOTE]
    > 當您啟動 **能源消耗** 分析工具時，您可能會看到 [ **使用者帳戶控制** ] 視窗要求您執行 *VsEtwCollector.exe* 的許可權。 選擇 [ **是**]。

3. 執行您的應用程式進行資料收集。

4. 若要停止分析，請切換回到 Visual Studio (Alt+Tab)，並選擇診斷中樞頁面上的 [ **停止收集** ]。

     ![停止收集資料](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio 會分析收集到的資料並顯示結果。

## <a name="collect-energy-profile-data-for-an-installed-app"></a>收集已安裝應用程式的能源分析資料
 [能源消耗] 工具只能在從 Visual Studio 方案啟動或從 Microsoft Store 安裝的 UWP 應用程式上執行。 方案在 Visual Studio 中開啟時，預設目標為 [ **啟始專案**]。 目標為已安裝的應用程式：

1. 選擇 [ **變更目標** ]，然後選擇 [ **已安裝的應用程式**]。

2. 從 [ **選取已安裝的應用程式套件** ] 清單中選擇目標。

3. 選擇 [效能分析工具] 頁面上的 [ **能源消耗** ]。

4. 選擇 [ **開始** ]，開始分析。

   若要停止分析，請切換回到 Visual Studio (Alt+Tab)，並選擇診斷中樞頁面上的 [ **停止收集** ]。

## <a name="analyze-energy-profile-data"></a>分析能源分析資料
 能源分析資料會顯示在 Visual Studio 文件視窗中：

 ![能源分析工具報表頁面](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|映像|描述|
|-|-|
|![步驟 1](../profiling/media/procguid_1.png "ProcGuid_1")|報告檔的名稱為 Report *YYYYMMDD-HHMM*.diagsession。 如果您決定儲存報告，可以變更名稱。|
|![步驟 2](../profiling/media/procguid_2.png "ProcGuid_2")|時間軸會顯示程式碼剖析工作階段的長度、應用程式週期啟用事件，以及使用者標記。|
|![步驟 3](../profiling/media/procguid_3.png "ProcGuid_3")|您可以拖曳藍色巡覽列，選取時間軸的區域，將報告限制在時間軸的一部分。|
|![步驟4](../profiling/media/procguid_4.png "ProcGuid_4")|[ **用電量** ] 圖形是多行折線圖，顯示程式碼剖析工作階段期間由裝置資源造成的電源輸出變更。 能源消耗分析工具會追蹤 CPU、網路活動和螢幕顯示器使用的電源。|
|![步驟5](../profiling/media/procguid_6.png "ProcGuid_6")|[ **資源 (開啟/關閉)**  ] 圖形提供網路能源成本的詳細資料。 [ **網路** ] 橫條圖表示網路連接開啟的時間。 [ **資料傳輸** ] 子橫條圖是應用程式透過網路接收或傳送資料的時間。|
|![步驟6](../profiling/media/procguid_6a.png "ProcGuid_6a")|[ **用電量摘要** ] 會顯示所選時間軸中 CPU、網路活動和螢幕顯示器使用的能源總計比例。|

 **若要分析能源分析資料**

 尋找資源用電量尖峰的區域。 將尖峰區與應用程式的功能產生關聯。 然後使用時間軸上的時間軸控制列放大該區域。 如果您將焦點放在網路使用方式，請展開 [ **資源 (開啟/關閉)** ] 圖形的 [ **網路**  ] 節點，比較網路連接開啟時間與應用程式透過連接接收或傳輸資料的時間。 減少在非必要時開啟網路，是非常有效的最佳化方式。

## <a name="optimize-energy-use"></a>最佳化能源利用
 除了傳輸資料之外，網路連線初始化、維護及關閉連線都會產生能源成本。 某些網路在資料已傳送或接收後仍然保持連線一段時間，以便讓更多資料透過單一連線傳輸。 您可以使用 [ **資源 (開啟/關閉)** ] 窗格檢查應用程式與連接互動的方式。

 ![&#47;關閉&#41; 窗格的資源 &#40;](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 如果 [ **網路** ] 和 [ **資料傳輸** ] 橫條圖顯示長時間開啟連接，間歇地傳送一系列的小型資料封包，您可以批次處理資料，使其在單一傳輸中傳送，減少開啟網路的時間，因此節省能源成本。

 ![能源消耗摘要窗格](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 對於顯示器的能源成本，您擁有的控制權比較少。 大部分畫面顯示淺色時，所需的能源比顯示深色更多，因此使用深色背景會是節省成本的一種方式。

## <a name="other-resources"></a>其他資源

- [C#/VB/C++ 和 XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) 的 **連線狀態和成本管理** 一節，描述提供網路連線資訊的 API，您的應用程式可使用此資訊將網路流量成本降至最低。

   UWP App 適用的 Visual Studio 模擬器可讓您模擬網路資訊 API 的資料連線屬性。 請參閱[在模擬器中執行 UWP App](../debugger/run-windows-store-apps-in-the-simulator.md)

- [CPU 使用量] 工具可以協助您降低因無效率函式所造成的 CPU 負載。 請參閱 [分析 CPU 使用量](../profiling/beginners-guide-to-performance-profiling.md)。

## <a name="see-also"></a>請參閱

- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)