---
title: I/O 時間 (執行緒檢視) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86c14292edcf8f132a14b67e931c5121105a9dc8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187437"
---
# <a name="io-time-threads-view"></a>I/O 時間 (執行緒檢視)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

時間軸中的這些區段與歸類為 I/O 的封鎖時間關聯。 這意謂著某個執行緒正等候 I/O 作業完成。 該執行緒可能已在 API 中被封鎖，或被「並行視覺化檢視」視為 I/O 的 I/O 相關核心等待封鎖。 `CreateFile()`、`ReadFile()` 及 `WSARecv()` 之類的 API 即屬於這個群組。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)
