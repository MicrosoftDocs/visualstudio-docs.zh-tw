---
title: 摘要檢視 - .NET 記憶體資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe6d3982828d1e2a8ae4aeaba3d89b1b75f4f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193323"
---
# <a name="summary-view---net-memory-data"></a>摘要檢視 - .NET 記憶體資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[摘要] 檢視顯示有關在程式碼剖析執行時，配置最多記憶體的 .NET 函式和類型資訊，以及建立次數最多的類型資訊。 如需包括通知連結和報表清單描述在內的詳細資訊，請參閱[摘要檢視](../profiling/summary-view.md)。  
  
## <a name="timeline-graph"></a>時間軸圖形  
 [摘要] 檢視的時間軸圖形會顯示已進行程式碼剖析的應用程式在程式碼剖析期間的處理器 (CPU) 使用率。 您可以使用時間軸圖形，將檢視篩選為選取的時間範圍。 如需詳細資訊，請參閱[如何：從摘要時間軸篩選報表檢視](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)。  
  
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
 [摘要檢視](../profiling/summary-view-sampling-data.md)   
 [摘要檢視](../profiling/summary-view-instrumentation-data.md)
