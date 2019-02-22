---
title: 睡眠時間 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e14fb1e90da5812d15cf36448b6c3f7283b5b87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992369"
---
# <a name="sleep-time"></a>睡眠時間
時間軸中的這些區段，會和分類為睡眠時間的封鎖時間相關聯。 睡眠分類表示執行緒自動放棄其邏輯核心，而且不執行任何工作。 在這段期間內，會在並行視覺化檢視當作睡眠分類計數的 API 中封鎖執行緒。 `Sleep()` 和 `SwitchToThread()` 這類 API 屬於這個群組。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)