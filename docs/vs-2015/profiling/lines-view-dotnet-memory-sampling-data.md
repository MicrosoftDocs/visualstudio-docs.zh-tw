---
title: 程式行檢視 - .NET 記憶體取樣資料 | Microsoft Docs
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
- Lines view
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3aa0c91cb6f26dd2a914195791c12421798c43b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486825"
---
# <a name="lines-view---net-memory-sampling-data"></a>程式行檢視 - .NET 記憶體取樣資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[程式行檢視-.NET 記憶體取樣資料](https://docs.microsoft.com/visualstudio/profiling/lines-view-dotnet-memory-sampling-data)。  
  
使用取樣方法之 .NET 記憶體配置分析資料的 [程式行] 檢視，會列出在執行分析期間配置記憶體的陳述式。 資料行也包含配置的大小和數量。  
  
 在原始程式檔中，陳述式在原始程式檔中可以長達多行，而單一行程式也可能包含一個以上的陳述式。  
  
 陳述式是由下列項目識別：  
  
-   包含此函式陳述式的原始程式檔。  
  
-   包含此陳述式的函式。  
  
-   此陳述式在原始程式檔中開始的行位置。  
  
-   此陳述式在原始程式檔中開始的字元。  
  
-   此陳述式在原始程式檔中結束的行位置。  
  
-   此陳述式在原始程式檔中結束的字元。  
  
 [程式行名稱] 資料行提供識別項資料的可排序串連。  
  
 根據定義，陳述式不會呼叫其他函式。 因此只會列出互斥值。  
  
|資料行|描述|  
|------------|-----------------|  
|**處理序 ID**|分析執行的處理序 ID (PID)。|  
|**處理序名稱**|處理序的名稱。|  
|**模組名稱**|包含陳述式的模組名稱。|  
|**模組路徑**|包含陳述式的模組路徑。|  
|**原始程式檔**|包含陳述式的原始程式檔。|  
|**函式名稱**|包含此陳述式的函式名稱。|  
|**函式行號**|原始程式檔中這個函式的開頭行號。|  
|**函式位址**|函式的開始位址。|  
|**原始程式碼開頭行**|發生配置的原始程式檔中的起始行號。|  
|**原始程式碼結尾行**|發生配置的原始程式檔中的結尾行號。|  
|**原始程式碼開頭字元**|發生配置的原始程式檔行中，起始字元的位移。|  
|**原始程式碼結尾字元**|發生配置的原始程式檔行中，結尾字元的位移。|  
|**程式行名稱**|分析工具產生的程式行識別項，該程式行使用下列語法：`Source File`**;[**`Line Number Start`**,**`Character Start`**]->;[**`Line Number Start,Character Start`**]**|  
|**專有配置**|已在此行中建立的物件總數。|  
|**專有配置 %**|分析執行期間，配置於此行中的物件佔所有已建立物件的百分比。|  
|**專有位元組**|在執行分析期間配置於此行中的記憶體位元組，佔所配置記憶體之所有位元組的百分比。|  
|**專有位元組 %**|在執行分析期間配置於此行中的記憶體位元組，佔所配置記憶體之所有位元組的百分比。|  
  
## <a name="see-also"></a>另請參閱  
 [程式行檢視](../profiling/lines-view-sampling-data.md)



