---
title: 空白時間表區段 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ff71dca6a4a590551909dc05357b80da32e18c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739867"
---
# <a name="empty-timeline-segment"></a>空白時間表區段
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在並行視覺化檢視中，時間表區段空白 (具有白色背景) 的原因取決於通道的類型。  
  
-   如為 CPU 執行緒通道，表示執行緒在時間表的這個部分不存在。 如果您對執行緒感興趣，您可以使用縮放控制項或水平捲動來尋找其執行區段。  
  
-   如為 I/O 通道，表示該時間點沒有代表目標處理序的磁碟存取發生。  
  
-   如為 DirectX 通道，表示在時間表的這個部分沒有代表目標處理序執行的 GPU 工作。  
  
-   如為標記通道，表示未產生任何標記。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒檢視](../profiling/threads-view-parallel-performance.md)   
 [縮放控制 (執行緒檢視)](../profiling/zoom-control-threads-view.md)



