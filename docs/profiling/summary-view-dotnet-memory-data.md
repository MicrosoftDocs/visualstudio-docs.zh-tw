---
title: 摘要檢視 - .NET 記憶體資料 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: f5f821f936ffa8e157eb61e5daab25d1421c6899
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935212"
---
# <a name="summary-view---net-memory-data"></a>摘要檢視 - .NET 記憶體資料
[摘要] 檢視顯示有關在程式碼剖析執行時，配置最多記憶體的 .NET 函式和類型資訊，以及建立次數最多的類型資訊。 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## <a name="timeline-graph"></a>時間軸圖形  
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的處理器 (CPU) 使用率。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[＜How to：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
## <a name="functions-allocating-most-memory"></a>配置最多記憶體的函式  
 列出在程式碼剖析執行時配置的記憶體位元組數最多的函式。  
  
|資料行|說明|  
|------------|-----------------|  
|**名稱**|函式的名稱。|  
|**位元組 %**|在程式碼剖析執行時，由此函式所配置或由此函式所呼叫的子函式配置的所有配置位元組數百分比。|  
  
## <a name="types-with-most-memory-allocated"></a>配置最多記憶體的類型  
 列出在程式碼剖析執行時配置的記憶體位元組數最多的類型。  
  
|資料行|說明|  
|------------|-----------------|  
|**名稱**|型別的名稱。|  
|**位元組 %**|在程式碼剖析執行時配置給此類型的所有配置位元組數百分比。|  
  
## <a name="types-with-most-instances"></a>具有最多執行個體的類型  
 列出在分析回合期間建立次數最多的類型。 具有  
  
|資料行|說明|  
|------------|-----------------|  
|**名稱**|型別的名稱。|  
|**執行個體 %**|在程式碼剖析執行時建立為此類型執行個體的 .NET 物件總數百分比。|  
  
## <a name="see-also"></a>另請參閱  
 [摘要檢視 - 取樣資料](../profiling/summary-view-sampling-data.md)   
 [摘要檢視 - 檢測資料](../profiling/summary-view-instrumentation-data.md)