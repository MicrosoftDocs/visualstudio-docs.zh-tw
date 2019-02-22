---
title: GPU 活動 (其他處理序) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c7d68547e0c2d0b056e2c60f1e9e183270841c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030258"
---
# <a name="gpu-activity-other-processes"></a>GPU 活動 (其他處理序)
[並行視覺化檢視] 中 [執行緒] 檢視的 [GPU 活動 (其他處理序)] 區段表示 GPU 代替系統中其他處理序處理要求的時間。 這些要求會以直接記憶體存取 (DMA) 封包格式傳送至 GPU。  區段的長度表示 GPU 處理封包的持續時間。  
  
 當您選取這種區段時，[目前] 索引標籤上的報告會顯示已處理封包的相關資訊。  此資訊包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出封包的處理序和處理封包所需的時間。