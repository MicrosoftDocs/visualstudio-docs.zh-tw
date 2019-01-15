---
title: 處理序檢視 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 104e34af7bd596b861fc3d1da1da193a6c1c373a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922042"
---
# <a name="process-view"></a>處理序檢視
處理序檢視顯示程式碼剖析執行期間所執行處理序和執行緒的程式碼剖析資料。  
  
 依名稱列出處理序。 處理序建立的執行緒會當成其子節點列出。 執行緒是由開始該執行緒的函式命名，或在沒有符號可以使用時，由標籤 **[ntdll.dll]** 命名。  
  
 若要新增或移除資料行，請在檢視中按一下滑鼠右鍵，然後選取 [新增/移除資料行]。 此外，您可以按一下資料行名稱來排序資料。 如需詳細資訊，請參閱[＜How to：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
 使用取樣和檢測方法所產生的資料和包括.NET 記憶體資料在內的資料，其處理序檢視的資料行都相同。 下表說明資料行的值。  
  
|資料行|說明|  
|------------|-----------------|  
|**唯一 ID**|分析工具產生的唯一處理程序或執行緒識別碼。|  
|**ID**|系統產生的處理序或執行緒識別碼。|  
|**名稱**|處理序或執行緒的名稱。|  
|**開始時間**|從程式碼剖析開始到處理序或執行緒開始的毫秒數或處理器週期數。|  
|**結束時間**|從程式碼剖析開始到處理序或執行緒結束的毫秒數或處理器週期數。|  
  
## <a name="see-also"></a>另請參閱  
 [取樣方法資料檢視](../profiling/profiler-sampling-method-data-views.md)   
 [檢測方法資料檢視](../profiling/instrumentation-method-data-views.md)   
 [.NET 記憶體資料檢視](../profiling/dotnet-memory-data-views.md)