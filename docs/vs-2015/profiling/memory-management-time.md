---
title: 記憶體管理時間 | Microsoft Docs
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
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9371c4d5249539c80299fd1b1573eba19c9dd14f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485293"
---
# <a name="memory-management-time"></a>記憶體管理時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[記憶體管理時間](https://docs.microsoft.com/visualstudio/profiling/memory-management-time)。  
  
時間軸中的這些區段會和分類為記憶體管理的封鎖時間相關聯。 這表示，和記憶體管理作業 (例如分頁) 相關聯的事件會封鎖執行緒。 在這段期間內，會在並行視覺化檢視當作記憶體管理分類計數的 API 或核心狀態中封鎖執行緒。 像是分頁和記憶體配置等事件都包括在內。  
  
 請檢查相關聯的呼叫堆疊並分析報表，以深入了解分類為記憶體管理的根本封鎖原因。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)



