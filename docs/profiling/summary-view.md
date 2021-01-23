---
title: 摘要檢視 | Microsoft Docs
description: 瞭解摘要視圖如何顯示分析回合中效能最高的函數或物件的相關資訊。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 154f168044e5395a534b4a79ea44d9eafe6293f6
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719275"
---
# <a name="summary-view"></a>摘要檢視
[摘要] 檢視顯示分析回合中效能耗費最多資源的函式或物件資訊。 此檢視會提供時間軸圖表，以及根據分析方法效能計量之兩個以上耗費最多資源的函式或物件清單。 此檢視中的資料取決於所使用的分析方法 (取樣、檢測或並行) 以及是否收集 .NET 記憶體配置。

 針對所有 [摘要] 檢視 (並行資料的 [摘要] 檢視除外)，[摘要] 檢視中的時間軸圖形會顯示已分析應用程式在分析期間的處理器 (CPU) 使用率。

- 如果您指定圖形上的時段，則可以重新分析該時段的資料，或將時間軸顯示縮放到您指定的時段。 如需詳細資訊，請參閱 [如何：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。

- 您可以按一下 [摘要] 檢視清單中的函式，以開啟函式的 [函式詳細資料] 檢視。 您也可以使用滑鼠右鍵按一下函式以取得其他檢視選項。

- 若要修改 [摘要檢視] 清單中所顯示的項目數，請開啟 [工具] 功能表，並指向 [選項]，然後按一下 [效能工具]。 在 [一般設定] 下方，修改 [摘要檢視中的函式數目] 設定。

## <a name="notifications-links"></a>通知連結
 您可以按一下 [通知] 清單中的連結，以設定報表的顯示選項。 清單是要時間軸圖形右側。

|選項|描述|
|-|-|
|**顯示非使用者程式碼**<br /><br /> **顯示 Just My Code**|不適用於原生程式碼或使用檢測方法所收集的分析資料。 切換只顯示使用者程式碼中的資料 ([顯示 Just My Code]) 以及顯示所有程式碼的資料 (包含系統程式碼) ([顯示非使用者程式碼])。 根據預設，會將資料限制為使用者程式碼。 若要變更設定，請參閱 [如何：篩選程式代碼剖析工具報表檢視以顯示 Just My Code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)。|
|**查看指引**|在 [錯誤清單] 視窗中顯示效能規則警告。 如需詳細資訊，請參閱[使用效能規則分析資料](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>報表
 您可以按一下 [報表] 清單中的連結以開啟不同的檢視，以及比較、儲存或篩選報表。 清單是要時間軸圖形右側。

|選項 |描述 |
|----------------------------| - |
| **顯示修改過的呼叫樹狀圖** | 顯示 [呼叫樹狀圖檢視] 中耗費最多資源的執行路徑。 如需詳細資訊，請參閱 [呼叫樹狀檢視](../profiling/call-tree-view.md)。 |
| **顯示熱門程式行** | 不適用於使用檢測方法所收集的分析資料。 在 [程式行檢視] 中，顯示耗費最多資源的原始程式碼行。 如需詳細資訊，請參閱[程式行檢視](../profiling/lines-view.md)。 |
| **比較報告** | 顯示 [選取要進行比較的分析檔案] 對話方塊，您可以在其中指定要與目前資料檔案比較的另一個分析資料檔案。 如需詳細資訊，請參閱[比較效能資料檔案](../profiling/comparing-performance-data-files.md)。 |
| **匯出報告資料** | 顯示 [匯出報告] 對話方塊，您可以在其中指定一或多個報表檢視以將另存為逗號分隔值 (.csv) 或 .xml 檔案。 如需詳細資訊，請參閱 [如何：匯出分析工具報表](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\))。 |
| **儲存分析的報告** | 將目前分析資料檔案儲存為 .vsps 檔案，這在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的介面中開啟地更為快速。 如需詳細資訊，請參閱 [如何：儲存已分析的分析資料檔](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))。 |
| **篩選報告資料** | 顯示分析報表篩選窗格，您可以在其中指定準則來限制報表檢視中的資料。 如需詳細資訊，請參閱 [效能報表檢視篩選](../profiling/performance-report-view-filter.md) |
| **切換全螢幕** | 切換報表檢視的全螢幕模式。 |

## <a name="see-also"></a>另請參閱
- [摘要視圖-取樣資料](../profiling/summary-view-sampling-data.md)
- [摘要視圖-檢測資料](../profiling/summary-view-instrumentation-data.md)
- [摘要視圖-.NET 記憶體資料](../profiling/summary-view-dotnet-memory-data.md)
