---
title: I/O 時間 (執行緒檢視) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50301149f844e0063deeb970e5bfb5bd46a55c1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="io-time-threads-view"></a>I/O 時間 (執行緒檢視)
時間軸中的這些區段與歸類為 I/O 的封鎖時間關聯。 這意謂著某個執行緒正等候 I/O 作業完成。 該執行緒可能已在 API 中被封鎖，或被「並行視覺化檢視」視為 I/O 的 I/O 相關核心等待封鎖。 `CreateFile()`、`ReadFile()` 及 `WSARecv()` 之類的 API 即屬於這個群組。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)