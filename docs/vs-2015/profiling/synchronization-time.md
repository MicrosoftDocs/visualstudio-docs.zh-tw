---
title: 同步處理時間 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790323"
---
# <a name="synchronization-time"></a>同步處理時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

時間軸中的這些區段會與歸類為同步處理的封鎖時間建立關聯。 當執行緒在同步處理中標記為已封鎖時，就會隱含這些項目的其中一個：  
  
- 執行此執行緒可能會造成呼叫眾所周知的執行緒同步處理 API，例如 `EnterCriticalSection()` 或 `WaitForSingleObject()`。  
  
- API 比對演算法無法真正面面俱到，因此有些可以對應到其他分類的 API 也可能會顯示為同步處理，因為呼叫堆疊中的框架最後會到達封鎖對應至此類別基本的基礎核心。  
  
  若要了解執行緒封鎖事件的根本原因，請仔細檢查封鎖的呼叫堆疊和分析報表。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)
