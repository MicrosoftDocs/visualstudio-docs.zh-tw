---
title: 睡眠時間 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "35668444"
---
# <a name="sleep-time"></a>睡眠時間
時間軸中的這些區段，會和分類為睡眠時間的封鎖時間相關聯。 睡眠分類表示執行緒自動放棄其邏輯核心，而且不執行任何工作。 在這段期間內，會在並行視覺化檢視當作睡眠分類計數的 API 中封鎖執行緒。 `Sleep()` 和 `SwitchToThread()` 這類 API 屬於這個群組。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)