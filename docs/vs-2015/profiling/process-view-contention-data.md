---
title: 處理序檢視 - 爭用資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e43541ddb75b067faa23437d315ce5f239256b1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180224"
---
# <a name="process-view---contention-data"></a>處理序檢視 - 爭用資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

處理序檢視顯示程式碼剖析執行期間所執行處理序和執行緒的爭用資料。  
  
 可以使用符號時，會依名稱列出處理序。 無法使用符號時，處理序會以十六進位格式列出其記憶體位址。 處理序建立的執行緒會當成其子系列出。  
  
 下表說明處理序檢視資料表中資料行的值。  
  
|資料行|描述|  
|------------|-----------------|  
|**開始時間**|從程式碼剖析開始到處理序或執行緒開始的毫秒數或處理器週期數。|  
|**封鎖時間**|處理序或執行緒的函式遭到封鎖而無法執行期間的時間總計。|  
|**封鎖時間 %**|就處理序或執行緒的存留期，處理序或執行緒的函式遭到封鎖而無法執行的時間所佔的百分比。|  
|**爭用**|處理序或執行緒的函式遭到封鎖而無法執行的次數。|  
|**爭用 %**|就程式碼剖析執行時的所有爭用，處理序或執行緒爭用所佔的百分比。|  
|**結束時間**|從程式碼剖析開始到處理序或執行緒結束的毫秒數或處理器週期數。|  
|**識別碼**|系統產生的處理序或執行緒識別碼。|  
|**存留時間**|從處理序或執行緒開始到處理序或執行緒結束，或到程式碼剖析結束的毫秒數或處理器週期數。|  
|**類型**|處理序或執行緒資料列的類型。<br /><br /> 僅在 **>vsreport** 命令列報表中。 如需詳細資訊，請參閱 [VSPerfReport](../profiling/vsperfreport.md)。|  
|**名稱**|處理序或執行緒的名稱。|  
|**唯一 ID**|分析工具產生的唯一處理程序或執行緒識別碼。|  
  
## <a name="see-also"></a>另請參閱  
 [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)   
 [處理序檢視](../profiling/process-view.md)
