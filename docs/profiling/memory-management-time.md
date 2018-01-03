---
title: "記憶體管理時間 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.paging
helpviewer_keywords: Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 08c111b89ee265820d314150ff28096eb9bf5d2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="memory-management-time"></a>記憶體管理時間
時間軸中的這些區段會和分類為記憶體管理的封鎖時間相關聯。 這表示，和記憶體管理作業 (例如分頁) 相關聯的事件會封鎖執行緒。 在這段期間內，會在並行視覺化檢視當作記憶體管理分類計數的 API 或核心狀態中封鎖執行緒。 像是分頁和記憶體配置等事件都包括在內。  
  
 請檢查相關聯的呼叫堆疊並分析報表，以深入了解分類為記憶體管理的根本封鎖原因。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)