---
title: 分析 UWP App 的網路使用量
description: 瞭解 Visual Studio Network diagnostics tool 如何收集使用 Http.sys API 所執行之網路作業的相關資料。
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45fa397d-d7a1-4c4c-9c97-ede6c21643bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 429bc6c8c2d82e3c18c75132f71e60231b10f10d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722902"
---
# <a name="analyze-network-usage-in-uwp-apps"></a>分析 UWP App 的網路使用量
Visual Studio 的 [網路] 診斷工具會收集使用 [Windows.Web.Http 應用程式開發介面](/uwp/api/windows.web.http)執行之網路作業的相關資料。 分析這份資料可協助您解決存取和驗證、不正確的快取使用，以及顯示和下載效能不佳等問題。

 [網路] 工具僅支援 UWP 應用程式。 目前不支援其他平台。

> [!NOTE]
> 如需更完整的網路工具描述，請參閱 [Visual Studio 的網路工具簡介](https://devblogs.microsoft.com/visualstudio/introducing-visual-studios-network-tool/)。

## <a name="collect-network-tool-data"></a>收集網路工具資料
 您應該針對 Visual Studio 電腦上開啟的 Visual Studio 專案執行 [網路] 工具。

1. 在 Visual Studio 中開啟專案。

2. 在功能表上，按一下 [ **Debug/效能分析工具**]。 選擇 [網路]，然後選擇 [啟動]。

3. 網路工具會開始收集您應用程式的 HTTP 流量。

    執行應用程式時，在左窗格中的摘要檢視會自動顯示擷取的 HTTP 作業清單。 在摘要檢視上選取項目，來檢視在右窗格詳細資料面板中的詳細資訊。

4. 選擇 [停止] 以關閉應用程式。

   報表視窗應該會類似這樣：

   ![[網路] 視窗](../profiling/media/network_fullwindow.png "NETWORK_FullWindow")

## <a name="analyze-data"></a>分析資料
 無論您的應用程式正在執行，或甚至在關閉之後，透過選取任何顯示在摘要檢視上的網路作業，即可分析擷取的 HTTP 流量。

 [網路] 摘要清單顯示執行應用程式時的每個網路作業資料。 選擇資料行標頭以排序清單，或選擇要顯示在 [內容類型] 篩選檢視中的內容類型。

 選擇 [另存為 HAR] 以建立可供 Fiddler 等協力廠商工具使用的 JSON 檔案。

 [網路] 詳細資料檢視在摘要檢視中顯示更多網路作業的相關資訊。

 ![網路工具詳細資料窗格](../profiling/media/network_detailsviewpane.png "NETWORK_DetailsViewPane")

|Name|描述|
|-|-|
|**標頭**|事件的要求標頭資訊。|
|**本文**|要求和回應承載資料。|
|**參數**|查詢字串參數名稱和值。|
|**餅乾**|回應和要求 Cookie 資料。|
|**時間**|取得所選資源的各階段圖表。|

 網路 [摘要] 列會顯示在任何給定的時間點、傳輸資料量、下載所花費時間，以及可見的錯誤數目 (4xx 或 5xx 回應的要求) 的網路作業數。

### <a name="analysis-tips"></a>分析秘訣
 此工具會反白顯示特定區域，有助您執行網路相關的分析：

1. 完全來自快取的要求會在 [已接收] 資料行中顯示為 [(從快取)]。 這可協助判斷您是否有效率地使用快取來節省使用者頻寬，或您是否意外地快取回應且提供具過時資料的應用程式給使用者。

2. 錯誤回應 (4xx 或 5xx) 會顯示在 [結果] 資料行中，並具有紅色狀態程式碼，同時也會在摘要列中反白顯示。 這樣可以在應用程式上許多潛在的要求之間輕易發現錯誤。

3. 回應美化顯示按鈕 (在主體索引標籤內) 可協助您藉由增加內容可讀性來剖析 JSON、XML、HTML、CSS、JavaScript 和 TypeScript 的回應承載。

## <a name="see-also"></a>另請參閱

- [使用或不使用偵錯工具來執行分析工具](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Visual Studio 部落格：Visual Studio 網路檢查簡介](https://devblogs.microsoft.com/visualstudio/)
- [Channel 9 影片： VS 診斷工具-新的網路分析工具](https://channel9.msdn.com/Series/ConnectOn-Demand/206)
- [Visual Studio 中的分析](../profiling/index.yml)
- [初步認識分析工具](../profiling/profiling-feature-tour.md)