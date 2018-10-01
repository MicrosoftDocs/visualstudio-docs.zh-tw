---
title: 函式檢視 - 爭用資料 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Functions view
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1250dfc781b57f3b289cbafc9d386b27b669ddf7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488632"
---
# <a name="functions-view---contention-data"></a>函式檢視 - 爭用資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[函式檢視-爭用資料](https://docs.microsoft.com/visualstudio/profiling/functions-view-contention-data)。  
  
爭用資料的函式報告檢視會列出執行的分析中，於分析執行期間被封鎖執行的函式。  
  
 下表說明分析資料檔 [函式] 檢視顯示的值，此檔案是使用並行方法收集。  
  
|資料行|描述|  
|------------|-----------------|  
|**專有封鎖時間**|此函式遭封鎖而無法執行函式主體程式碼的時間。 不包括由該函式所呼叫函式的封鎖時間。|  
|**專有封鎖時間 %**|在分析執行的所有封鎖時間中，屬於此函式的專屬封鎖時間百分比。|  
|**專有爭用**|此函式已遭封鎖，無法執行函式主體程式碼的次數。 不包含由該函式所呼叫函式中的爭用。|  
|**專有爭用 %**|在分析執行的所有爭用中，屬於此函式的專屬爭用百分比。|  
|**函式位址**|函式的位址。|  
|**函式名稱**|函式的完整格式名稱。|  
|**內含封鎖時間**|此函式或此函式所呼叫函式已遭封鎖而無法執行的時間。|  
|**內含封鎖時間 %**|在分析執行的所有封鎖時間中，屬於此函式或模組的內含封鎖時間百分比。|  
|**內含爭用**|此函式或此函式所呼叫函式已遭封鎖而無法執行的次數。|  
|**內含爭用 %**|在分析執行的所有爭用中，屬於此函式或模組的內含爭用百分比。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**模組名稱**|包含該函式的模組名稱。|  
|**模組路徑**|包含該函式的模組路徑。|  
|**處理序 ID**|函式於該處理序中執行的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**原始程式檔**|含有這個函式定義的原始程式檔。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [函式檢視](../profiling/functions-view.md)   
 [函式檢視 - 檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [函式檢視 - 取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [函式檢視](../profiling/functions-view-instrumentation-data.md)   
 [函式檢視](../profiling/functions-view-sampling-data.md)



