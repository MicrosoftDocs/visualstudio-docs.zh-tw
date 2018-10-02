---
title: 處理序檢視 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6d0c560cdd40651763837bba4e87372eba76007
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489384"
---
# <a name="process-view"></a>處理序檢視
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[處理序檢視](https://docs.microsoft.com/visualstudio/profiling/process-view)。  
  
處理序檢視顯示程式碼剖析執行期間所執行處理序和執行緒的程式碼剖析資料。  
  
 依名稱列出處理序。 處理序建立的執行緒會當成其子節點列出。 執行緒是由開始該執行緒的函式命名，或在沒有符號可以使用時，由標籤 **[ntdll.dll]** 命名。  
  
 若要新增或移除資料行，請在檢視中按一下滑鼠右鍵，然後選取 [新增/移除資料行]。 此外，您可以按一下資料行名稱來排序資料。 如需詳細資訊，請參閱[如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)。  
  
 使用取樣和檢測方法所產生的資料和包括.NET 記憶體資料在內的資料，其處理序檢視的資料行都相同。 下表說明資料行的值。  
  
|資料行|描述|  
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



