---
title: 指令指標 (IP) 檢視 - 爭用資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b27b185e659fc3a1f0adca4379896543a1eb87ea
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834578"
---
# <a name="instruction-pointers-ips-view---contention-data"></a>指令指標 (IP) 檢視 - 爭用資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

爭用資料的 IP檢視會列出遭到封鎖而不可在程式碼剖析執行時執行的組件指令。  
  
 下表說明指令指標檢視中各資料行的值。  
  
|資料行|說明|  
|------------|-----------------|  
|**專有封鎖時間**|這個函式中的封鎖時間。|  
|**專有封鎖時間 %**|指令執行時的封鎖時間百分比。|  
|**專有爭用**|指令執行時所發生爭用情況的數目。|  
|**專有爭用 %**|指令執行時，在程式碼剖析執行時所發生所有爭用情況的百分比。|  
|**函式位址**|在載入的二進位檔中函式的起始記憶體位址。|  
|**函式名稱**|包含此指令的函式名稱。|  
|**指令位址**|載入的二進位檔中指令的記憶體位址。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**模組名稱**|包含該指令的模組名稱。|  
|**模組路徑**|包含該指令的模組路徑。|  
|**處理序 ID**|已進行程式碼剖析之處理序的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**原始程式碼開頭字元**|此指令開始的原始程式檔行中的字元位移。|  
|**原始程式碼結尾字元**|此指令結束的原始程式檔行中的字元位移。|  
|**原始程式檔**|包含此指令的原始程式檔。|  
|**原始程式碼開頭行**|此函式在原始程式檔中開始的行號。|  
|**原始程式碼結尾行**|此函式在原始程式檔中結束的行號。|  
  
## <a name="see-also"></a>請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [指令指標 (IP) 檢視](../profiling/instruction-pointers-ips-view.md)   
 [指令指標 (IP) 檢視 - 取樣](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [指令指標 (IP) 檢視](../profiling/instruction-pointers-ips-view-sampling-data.md)
