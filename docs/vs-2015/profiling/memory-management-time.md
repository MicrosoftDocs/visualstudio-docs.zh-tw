---
title: 記憶體管理時間 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48cbdd523f4527af84c52366a439a18330e1828c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54752057"
---
# <a name="memory-management-time"></a>記憶體管理時間
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

時間軸中的這些區段會和分類為記憶體管理的封鎖時間相關聯。 這表示，和記憶體管理作業 (例如分頁) 相關聯的事件會封鎖執行緒。 在這段期間內，會在並行視覺化檢視當作記憶體管理分類計數的 API 或核心狀態中封鎖執行緒。 像是分頁和記憶體配置等事件都包括在內。  
  
 請檢查相關聯的呼叫堆疊並分析報表，以深入了解分類為記憶體管理的根本封鎖原因。  
  
## <a name="see-also"></a>請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)
