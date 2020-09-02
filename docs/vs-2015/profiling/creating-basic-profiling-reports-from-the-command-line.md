---
title: 從命令列建立基本的分析報告 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537177"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>從命令列建立基本的分析報告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題描述基本的 VSPerfReport 命令，它們會從 .vsp、.vsps 分析資料檔案產生逗號分隔值 (.csv) 的報告。 如需所有報表選項的說明，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。  
  
## <a name="report-commands"></a>報表命令  
 使用下列命令之一建立指定的分析資料檔報表。  
  
 **VSPerfReport** `VSPFile` **/Summary:All**  
 產生可供 .vsp 或.vsps 檔案使用的所有報表。  
  
 **VSPerfReport** `VSPFile`**/Summary：** `ReportType`[,`ReportType`...]  
 產生指定的報表類型。  
  
 **VSPerfReport** `VSPFile` **/CallTrace**  
 產生列出每個資料收集事件的報表。 僅檢測。  
  
## <a name="summary-report-type-parameters"></a>摘要報表型別參數  
 下表描述由指定的報表類型選項所產生的報表。 報表中的欄位取決於收集資料所使用的分析方法。  
  
|摘要參數|報表說明|報表參考|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|代表函式之間的父/子關聯性。|-   [取樣資料](../profiling/caller-callee-view-sampling-data.md)<br />-   [檢測資料](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|依函式列出程式碼剖析資料。|-   [取樣資料](../profiling/functions-view-sampling-data.md)<br />-   [檢測資料](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/functions-view-contention-data.md)|  
|**呼叫樹狀結構**|表示執行路徑以及分析執行中的函式分析資料。|-   [檢測資料](../profiling/call-tree-view-instrumentation-data.md)<br />-   [取樣資料](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/call-tree-view-contention-data.md)|  
|**計數器**|列出分析執行期間所收集的分析標記以及 Windows 效能計數器值。|-   [標記視圖](../profiling/marks-view.md)|  
|**Ip**|依指令列出分析資料。|-   [取樣資料](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [爭用資料](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**存留期**|列出配置物件的存留期。|-   [物件存留期視圖](../profiling/object-lifetime-view.md)|  
|**線條**|按原始程式碼列出分析資料。|-   [取樣資料](../profiling/lines-view-sampling-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [爭用資料](../profiling/lines-view-contention-data.md)|  
|**標頭**|分析資料檔案標頭資訊。|檔案專用。|  
|**標記**|在分析執行中收集的分析標記。|-   [標記視圖](../profiling/marks-view.md)|  
|**模組**|列出模組的分析資料。|-   [取樣資料](../profiling/modules-view-sampling-data.md)<br />-   [檢測資料](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET 記憶體取樣資料](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET 記憶體檢測資料](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [爭用資料](../profiling/modules-view-contention-data.md)|  
|**處理**|列出處理序的分析資料。|-   [進程視圖](../profiling/process-view.md)<br />-   [爭用資料](../profiling/process-view-contention-data.md)|  
|**執行緒**|列出執行序的分析資料。|-   [進程視圖](../profiling/process-view.md)|  
|**類型**|依類型列出配置的分析資料。|-   [配置視圖](../profiling/dotnet-memory-allocations-view.md)|  
|**爭論**|資源爭用。|-   [資源爭用](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|列出效能規則問題。|-   列出規則問題的 CheckId、描述和原始程式碼位置。|  
|**ETW**|列出分析執行中所收集的 Windows 事件追蹤 (ETW) 事件。|-   [ETW 報表](../profiling/event-tracing-for-windows-etw-report.md)|
