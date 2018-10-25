---
title: 了解檢測資料值 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75a1fddc6195805b786f4ad343c1c8917129dcdb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949229"
---
# <a name="understanding-instrumentation-data-values"></a>認識檢測資料值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的「檢測」分析方法會記錄已進行程式碼剖析的應用程式中函式呼叫、程式碼及指示的詳細計時資訊  
  
 **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  檢測方法會在已進行程式碼剖析的二進位檔中目標函式的開始和結束處，以及在那些函式每次呼叫其他函式的前後插入程式碼。 插入程式碼會記錄下列項目︰  
  
- 此收集事件與前一個事件之間的間隔。  
  
- 作業系統在間隔期間是否曾執行作業。 例如，作業系統可能會讀取或寫入磁碟，或在目標執行緒與另一個處理序中的另一個執行緒之間切換。  
  
  **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  對於每個間隔，分析工具會重新建構出現在間隔結尾的呼叫堆疊。 呼叫堆疊是某時間點在處理器上作用中的函式清單。 只有一個函式 (目前的函式) 在執行程式碼。其他函式是導致呼叫目前函式 (呼叫堆疊) 的函式呼叫鏈結。  
  
  對於呼叫堆疊上的每個函式，在記錄間隔時，分析工具分析會將間隔加入至函式的四個資料值之一或多個值。 分析會根據兩項準則將間隔加入至函式的資料值：  
  
- 函式程式碼或「子函式」 (由該函式呼叫的函式) 中是否發生間隔。  
  
- 間隔中是否發生作業系統事件。  
  
  函式間隔的資料值或資料範圍稱為「功能內含耗用」、「功能專屬耗用」、「應用程式內含」及「應用程式專屬」：  
  
- 函式的所有間隔都會加入至功能內含耗用資料值。  
  
- 如果間隔發生在函式的程式碼中，而不是子函式中，會將間隔加入至函式的功能專屬耗用資料值。  
  
- 如果間隔中未發生作業系統事件，會將間隔加入到應用程式內含資料值。  
  
- 如果間隔內並未發生作業系統事件，而是在直接執行函式程式碼時發生間隔 (也就是未發生在子函式中)，會將間隔加入至應用程式專屬資料值。  
  
  程式碼剖析工具報表彙總程式碼剖析工作階段本身以及工作階段的處理序、執行緒及二進位檔中函式的總值。  
  
## <a name="elapsed-inclusive-values"></a>功能內含耗用值  
 花費在執行函式和其子函式的時間總計。  
  
 功能內含耗用值包括花費在直接執行函式程式碼的時間間隔，以及執行目標函式的子函式所花費的時間間隔。 函式和其子函式的間隔，包括等候作業系統的時間也包含在功能內含耗用值內。  
  
## <a name="elapsed-exclusive-values"></a>功能專屬耗用值  
 花費在執行函式的時間，但不包括花費在子函式的時間。  
  
 功能專屬耗用值包括花費在直接執行函式程式碼的時間間隔，不論是間隔內是否發生作業系統事件。 功能專屬耗用值不包含花費在目標函式所呼叫子函式的所有時間間隔。  
  
## <a name="application-inclusive-values"></a>應用程式內含值  
 花費在執行函式和其子函式的時間，但不包括花費在作業系統事件的時間。  
  
 應用程式內含值不包括含有作業系統事件的間隔。 應用程式內含值包括花費在執行函式的所有其他時間間隔，不論是花費在直接執行函式程式碼的時間間隔，或者執行目標函式的子函式所花費的時間間隔。  
  
## <a name="application-exclusive-values"></a>應用程式專屬值  
 花費在執行函式的時間，但不包括花費在子函式的時間，以及花費在作業系統事件的時間。  
  
 應用程式專屬值不包括含有作業系統事件的間隔，或花費在執行由函式所呼叫函式的時間間隔。 應用程式專屬值只包括那些花費在直接執行函式程式碼的時間間隔，但不包含作業系統事件。  
  
## <a name="elapsed-inclusive-percent"></a>功能內含耗用百分比  
 函式、模組、執行緒或處理序的功能內含耗用值的程式碼剖析工作階段功能內含耗用值總計百分比。  
  
 100 * 函式功能內含耗用 / 工作階段功能內含耗用  
  
## <a name="elapsed-exclusive-percent"></a>功能專屬耗用百分比  
 函式、模組、執行緒或處理序的功能專屬耗用值的程式碼剖析工作階段功能內含耗用值總計百分比。  
  
 100 * 函式功能專屬耗用 / 工作階段功能內含耗用  
  
## <a name="application-inclusive-percent"></a>應用程式內含百分比  
 函式、模組、執行緒或處理序的應用程式內含值的程式碼剖析工作階段應用程式內含值總計百分比。  
  
 100 * 函式應用內含 / 工作階段應用程式內含  
  
## <a name="application-exclusive-percent"></a>應用程式專屬百分比  
 函式、模組、執行緒或處理序的應用程式專屬值的程式碼剖析工作階段應用程式內含值總計百分比。  
  
 100 * 函式應用程式專屬 / 工作階段應用程式內含  
  
## <a name="see-also"></a>另請參閱  
 [分析效能工具資料](../profiling/analyzing-performance-tools-data.md)   
 [如何：選擇收集方法](../profiling/how-to-choose-collection-methods.md)



