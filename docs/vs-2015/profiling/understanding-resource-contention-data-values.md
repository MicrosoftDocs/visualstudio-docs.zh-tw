---
title: 了解資源爭用資料值 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
ms.assetid: 071c0f0f-1eba-4dc8-ae87-0810e4086dd0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5983396924f38c31b6dafcd42b762042e1880e8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145440"
---
# <a name="understanding-resource-contention-data-values"></a>認識資源爭用資料值
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

資源爭用分析會在每次強迫應用程式中的競爭執行緒等候共用資源的存取權時，收集詳細的呼叫堆疊資訊。  
  
 **需求**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、[!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、[!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  資源爭用報表可顯示爭用總數，以及等候資源以用於發生等候的模組、函式、原始碼程式行及指示所花費的總時間。  
  
- 內含值會顯示因資源爭用而強制函式等候爭用總數，以及該函式的總等候時間。  內含值中會包含由該函式所呼叫子函式造成的爭用情況。  
  
- 專有值只顯示強制函式等候和由函式主體中的程式碼所造成的爭用數目。 不包括由子函式造成的爭用情況。 函式的專有時間也只包括函式主體中陳述式所造成的等候時間。  
  
  資源爭用報表檢視也會包含一個時間軸圖形，顯示一段時間內的個別爭用事件，以及顯示建立特定事件的呼叫堆疊。 如需詳細資訊，請參閱下列其中一個主題：  
  
- [執行緒詳細資料檢視](../profiling/thread-details-view-contention-data.md)  
  
- [資源詳細資料檢視](../profiling/resource-details-view-contention-data.md)  
  
  如需並行程式碼剖析第二個模式的詳細資訊，請參閱[並行視覺化檢視](../profiling/concurrency-visualizer.md)。
