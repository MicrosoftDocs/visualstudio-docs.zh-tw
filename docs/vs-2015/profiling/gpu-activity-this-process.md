---
title: GPU 活動 (這個處理序) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc7741e46d9b7ae3bf7e53e6a07f5601e7dbbd83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499627"
---
# <a name="gpu-activity-this-process"></a>GPU 活動 (這個處理序)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[GPU 活動 （這個處理序）](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-this-process)。  
  
[並行視覺化檢視] 中 [執行緒] 檢視的 [GPU 活動 (這個處理序)] 區段表示 GPU 代替目前的處理序處理要求的時間。 這些要求會以直接記憶體存取 (DMA) 封包格式傳送至 GPU。 區段的長度表示 GPU 代替目前的處理序處理 DMA 封包的時間。  
  
 當您選取 GPU 活動區段時，[目前] 索引標籤上的報告會顯示已處理的 DMA 封包的相關資訊。 此資訊包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出封包的處理序和處理封包所需的時間。 目前的處理序以外的處理序可能已將 DMA 封包實際送交 GPU 。 [並行視覺化檢視] 可以偵測到另一個處理序代替目前的處理序送出工作給 GPU。



