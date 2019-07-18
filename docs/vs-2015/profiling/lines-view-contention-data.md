---
title: 程式行檢視 - 爭用資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb6b8191b39bfc79615bf0bbcd4fb469395f8d8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583154"
---
# <a name="lines-view---contention-data"></a>程式行檢視 - 爭用資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

爭用資料的 [程式行] 檢視會針對在執行分析期間收集樣本時執行的陳述式，列出效能資料。 在原始程式檔中，陳述式在原始程式檔中可以長達多行，而單一行程式也可能包含一個以上的陳述式。  
  
 陳述式是由下列資料識別：  
  
- 包含此函式陳述式的原始程式檔。  
  
- 包含此陳述式的函式。  
  
- 此陳述式在原始程式檔中開始的行位置。  
  
- 此陳述式在原始程式檔中開始的字元。  
  
- 此陳述式在原始程式檔中結束的行位置。  
  
- 此陳述式在原始程式檔中結束的字元。  
  
  [程式行名稱] 資料行提供識別項資料的可排序串連。  
  
  下表說明 [程式行] 檢視報表的資料行。  
  
|資料行|說明|  
|------------|-----------------|  
|**專有封鎖時間**|此陳述式因爭用事件遭封鎖，無法在陳述式中執行程式碼的時間長度。 陳述式所呼叫函式中的封鎖時間不包括在內。|  
|**專有封鎖時間 %**|陳述式的專有封鎖時間佔處理序中所有封鎖時間的百分比。|  
|**專有爭用**|此陳述式因爭用事件遭封鎖，無法在陳述式中執行程式碼的次數。 陳述式所呼叫函式中的爭用事件不包括在內。|  
|**專有爭用 %**|此陳述式的專有爭用佔處理序中所有爭用事件的百分比。|  
|**函式位址**|包含此陳述式的函式位址。|  
|**函式名稱**|包含此陳述式的函式完整名稱。|  
|**內含封鎖時間**|此陳述式以及陳述式中所呼叫函式的封鎖時間。|  
|**內含封鎖時間 %**|陳述式的內含封鎖時間佔處理序中所有封鎖時間的百分比。|  
|**內含爭用**|此陳述式及陳述式中所呼叫的函式遭封鎖而無法執行的次數。|  
|**內含爭用 %**|此陳述式的內含爭用佔處理序中所有爭用事件的百分比。|  
|**程式行名稱**|分析工具產生的程式行識別項。 此識別項使用下列語法：`SourceFile`**;[**`LineNumberStart`**,**`CharacterStart`**]->;[**`LineNumberEnd`**,**`CharacterEnd`**]**|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**模組名稱**|包含陳述式的模組名稱。|  
|**模組路徑**|包含陳述式的模組路徑。|  
|**處理序 ID**|已進行程式碼剖析之處理序的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**原始程式碼開頭字元**|原始程式檔中，此陳述式開始之程式行中起始字元的位移。|  
|**原始程式碼結尾字元**|原始程式檔中，此陳述式結束之程式行中起始字元的位移。|  
|**原始程式檔**|包含函式陳述式之原始程式檔的名稱。|  
|**原始程式碼開頭行**|此陳述式在原始程式檔中開始的行號。|  
|**原始程式碼結尾行**|此陳述式在原始程式檔中結束的行號。|  
  
## <a name="see-also"></a>請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [程式行檢視](../profiling/lines-view.md)   
 [程式行檢視 - 取樣](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [程式行檢視](../profiling/lines-view-sampling-data.md)
