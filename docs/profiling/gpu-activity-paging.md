---
title: GPU 活動 (分頁) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bd28c7b41a01992ad52fa343b098b0a02460806
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969611"
---
# <a name="gpu-activity-paging"></a>GPU 活動 (分頁)
[執行緒]**** 索引標籤上的 [GPU 活動 (分頁)]**** 區段表示 GPU 處理分頁要求的時間。  區段的長度表示 GPU 處理直接記憶體存取 (DMA) 分頁封包的持續時間。 一般來說，分頁封包與 CPU 和 GPU 之間的記憶體傳輸相關聯。

 當您選取 GPU 分頁區段時，[目前]**** 索引標籤上的報告會顯示已處理的 DMA 封包的相關資訊。 這包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出 DMA 封包的處理序和處理封包所需的時間。

## <a name="see-also"></a>另請參閱
- [使用率檢視](../profiling/utilization-view.md)