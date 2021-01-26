---
title: GPU 活動 (這個處理序) | Microsoft Docs
description: 在並行處理常式的 [執行緒] 視圖中，閱讀 (此程式) 區段的 GPU 活動相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcfc96f9b29b8fae3bf9a97273ed6c675d1655fb
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801173"
---
# <a name="gpu-activity-this-process"></a>GPU 活動 (這個處理序)
[並行視覺化檢視] 中 [執行緒] 檢視的 [GPU 活動 (這個處理序)] 區段表示 GPU 代替目前的處理序處理要求的時間。 這些要求會以直接記憶體存取 (DMA) 封包格式傳送至 GPU。 區段的長度表示 GPU 代替目前的處理序處理 DMA 封包的時間。

 當您選取 GPU 活動區段時，[目前] 索引標籤上的報告會顯示已處理的 DMA 封包的相關資訊。 此資訊包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出封包的處理序和處理封包所需的時間。 目前的處理序以外的處理序可能已將 DMA 封包實際送交 GPU 。 [並行視覺化檢視] 可以偵測到另一個處理序代替目前的處理序送出工作給 GPU。