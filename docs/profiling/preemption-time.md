---
title: 先佔時間 | Microsoft Docs
description: 瞭解 Premption 時間，並將時間軸中的這些區段與歸類為預先搶佔的封鎖時間相關聯。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a102b11fdc7608b94b97105b061e28860f41a9a1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719509"
---
# <a name="preemption-time"></a>先佔時間
時間軸中的這些區段，會和分類為先佔的封鎖時間建立關聯。 此分類表示執行緒因為下列原因之一而被切換︰

- 排程器已使用較高優先順序的執行緒取代它。

- 執行緒的執行配量已到期，而其他執行緒已準備好執行。

  在這段期間內，執行緒因為並行視覺化檢視被視作先佔的核心等候原因而被封鎖。 先佔區段會在執行緒被推出邏輯核心時開始，並會在該執行緒繼續執行時結束。

  先佔區段的工具提示會顯示造成先佔的處理序或執行緒名稱。 不過，這不表示接手的處理序或執行緒會在先佔期間全程執行。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)