---
title: 了解記憶體配置和物件存留期資料值 | Microsoft Docs
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
- .NET memory profiling method
- Profiling Tools, .NET memory method
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3df4fe3189078da07f282b6f323ca697c763a08b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793720"
---
# <a name="understanding-memory-allocation-and-object-lifetime-data-values"></a>認識記憶體配置和物件存留期資料值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 程式碼剖析工具的 *.NET 記憶體配置*程式碼剖析方法收集在配置時建立或在記憶體回收時終結的物件大小和數目相關資訊，以及事件發生時有關函式「呼叫堆疊」的其他資訊。 「呼叫堆疊」是一個動態結構，其中儲存在處理器上執行的函式相關資訊。  
  
 **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  記憶體分析工具會在每次於已進行程式碼剖析的應用程式中配置 .NET Framework 物件時，中斷電腦處理器。 也會收集物件存留期資料時，分析工具會在每次 .NET Framework 記憶體回收之後中斷處理器。 針對每個已分析的函式和每種物件類型彙總資料。  
  
## <a name="allocation-data"></a>配置資料  
 發生 .memory 事件時，已配置或已終結的記憶體物件總計數與大小都會遞增。  
  
 發生 .memory 配置事件時，分析工具會讓呼叫堆疊上每個函式的樣本計數遞增。 在收集資料時，呼叫堆疊上只有一個函式目前正在其函式主體中執行程式碼。 堆疊上的其他函式則是函式呼叫階層中的父代，會等候它們呼叫的函式傳回。  
  
-   對於配置事件，該分析工具會讓目前正在執行其指示的函式「專有」樣本計數遞增。 因為專有樣本也是函式總 (內含) 樣本數的一部分，所以目前作用中函式的內含樣本計數也會遞增。  
  
-   分析工具會讓呼叫堆疊上所有其他函式的內含樣本計數遞增。  
  
## <a name="lifetime-data"></a>存留期資料  
 .NET Framework 的記憶體回收行程可管理應用程式的記憶體配置及釋放。 為了要最佳化記憶體回收行程的效能，Managed 堆積分成三個層代 (Generation)：0、1 和 2。 執行階段的記憶體回收行程會將新的物件儲存在層代 0。 在回收之後存留下來的物件則會升階並儲存在層代 1 與 2。  
  
 記憶體回收行程會取消配置整個物件層代來回收記憶體。 對於已進行程式碼剖析的應用程式建立的物件，物件存留期檢視會顯示物件的數目和大小，以及回收時的層代。



