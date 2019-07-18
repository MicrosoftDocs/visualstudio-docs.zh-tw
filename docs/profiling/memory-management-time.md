---
title: 記憶體管理時間 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 442973edb18e75bafda8a9397eac799286c69dfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963777"
---
# <a name="memory-management-time"></a>記憶體管理時間
時間軸中的這些區段會和分類為記憶體管理的封鎖時間相關聯。 這個案例表示，和記憶體管理作業 (例如分頁) 建立關聯的事件會封鎖執行緒。 在這段期間內，會在並行視覺化檢視當作記憶體管理分類計數的 API 或核心狀態中封鎖執行緒。 像是分頁和記憶體配置等事件都包括在內。

 請檢查相關聯的呼叫堆疊並分析報表，以深入了解分類為記憶體管理的根本封鎖原因。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)