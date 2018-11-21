---
title: 執行分析報表 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c211271bbc4be147d22ab4cb0262b591f4b839a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763609"
---
# <a name="execution-profile-report"></a>執行分析報表
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

執行分析報表是傳統的取樣分析。 當執行緒在邏輯核心上執行時，約每毫秒會擷取一次樣本，並行視覺化檢視會透過自動分頁累積的樣本堆疊集來建立典型的呼叫樹狀圖。 目前的時間範圍、隱藏的執行緒及下列可套用的篩選都可能影響此資料表中的資料︰  
  
- 如果已選取 Just My Code，只會顯示有使用者程式碼的堆疊框架，再加上使用者程式碼下方的一個層級。  
  
- 如果已設定 Noise 減少值，報表會篩掉小於指定頻率的自動分頁堆疊。  
  
  下表顯示報表中的資料行。  
  
|資料行|描述|  
|------------|-----------------|  
|名稱|每個層級的呼叫堆疊的函式名稱。|  
|內含樣本|針對到呼叫堆疊樹狀圖的這個層級為止的所有堆疊收集的樣本總數。 此內含數字是此函式的專屬樣本和其所有子節點的內含計數器的總和。|  
|專有樣本|收集的樣本總數，其中，此函式是呼叫堆疊的最低層級。|  
|內含 %|內含樣本資料行中顯示的樣本總數百分比。 百分比會四捨五入成兩個小數位數。|  
|專有 %|專有樣本資料行中顯示的樣本總數百分比。 百分比會四捨五入成兩個小數位數。|  
|詳細資料|函式的完整格式名稱。 當有詳細資料可用時，其中會包括行數。|  
  
 在[執行時間 (執行緒檢視)](../profiling/execution-time-threads-view.md) 檢視中可以看到此報表的資料表。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)



