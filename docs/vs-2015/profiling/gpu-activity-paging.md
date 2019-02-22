---
title: GPU 活動 (分頁) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54769083"
---
# <a name="gpu-activity-paging"></a>GPU 活動 (分頁)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[執行緒] 索引標籤上的 [GPU 活動 (分頁)] 區段表示 GPU 處理分頁要求的時間。  區段的長度表示 GPU 處理直接記憶體存取 (DMA) 分頁封包的持續時間。 一般來說，分頁封包與 CPU 和 GPU 之間的記憶體傳輸相關聯。  
  
 當您選取 GPU 分頁區段時，[目前] 索引標籤上的報告會顯示已處理的 DMA 封包的相關資訊。 這包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出 DMA 封包的處理序和處理封包所需的時間。  
  
## <a name="see-also"></a>請參閱  
 [使用率檢視](../profiling/utilization-view.md)
