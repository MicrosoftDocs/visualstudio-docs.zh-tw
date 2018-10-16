---
title: 同步處理時間 | Microsoft Docs
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
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d7fe50e8b678e6baa02deeab5f111c71645dbb4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219722"
---
# <a name="synchronization-time"></a>同步處理時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

時間軸中的這些區段會與歸類為同步處理的封鎖時間建立關聯。 當執行緒在同步處理中標記為已封鎖時，就會隱含這些項目的其中一個：  
  
-   執行此執行緒可能會造成呼叫眾所周知的執行緒同步處理 API，例如 `EnterCriticalSection()` 或 `WaitForSingleObject()`。  
  
-   API 比對演算法無法真正面面俱到，因此有些可以對應到其他分類的 API 也可能會顯示為同步處理，因為呼叫堆疊中的框架最後會到達封鎖對應至此類別基本的基礎核心。  
  
 若要了解執行緒封鎖事件的根本原因，請仔細檢查封鎖的呼叫堆疊和分析報表。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)



