---
title: I/O 時間 (執行緒檢視) | Microsoft Docs
description: 瞭解 i/o 時間區段如何與以 i/o 分類的封鎖時間相關聯，這表示執行緒正在等候 i/o 作業完成。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906861"
---
# <a name="io-time-threads-view"></a>I/O 時間 (執行緒檢視)
時間軸中的這些區段與歸類為 I/O 的封鎖時間關聯。 這意謂著某個執行緒正等候 I/O 作業完成。 該執行緒可能已在 API 中被封鎖，或被「並行視覺化檢視」視為 I/O 的 I/O 相關核心等待封鎖。 `CreateFile()`、`ReadFile()` 及 `WSARecv()` 之類的 API 即屬於這個群組。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)