---
title: 睡眠時間 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4d12097a8bf952cc0af0fa99025b9747ee7b3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498693"
---
# <a name="sleep-time"></a>睡眠時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[睡眠時間](https://docs.microsoft.com/visualstudio/profiling/sleep-time)。  
  
時間軸中的這些區段，會和分類為睡眠時間的封鎖時間相關聯。 睡眠分類表示執行緒自動放棄其邏輯核心，而且不執行任何工作。 在這段期間內，會在並行視覺化檢視當作睡眠分類計數的 API 中封鎖執行緒。 `Sleep()` 和 `SwitchToThread()` 這類 API 屬於這個群組。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)



