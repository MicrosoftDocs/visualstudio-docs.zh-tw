---
title: "睡眠時間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.sleep
helpviewer_keywords: Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4385fd42c14d13e83f85683ef33a613fd6f78765
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sleep-time"></a>睡眠時間
時間軸中的這些區段，會和分類為睡眠時間的封鎖時間相關聯。 睡眠分類表示執行緒自動放棄其邏輯核心，而且不執行任何工作。 在這段期間內，會在並行視覺化檢視當作睡眠分類計數的 API 中封鎖執行緒。 `Sleep()` 和 `SwitchToThread()` 這類 API 屬於這個群組。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)