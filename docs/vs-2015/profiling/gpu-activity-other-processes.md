---
title: GPU 活動 (其他處理序) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a3b0e97d82d67916aa71f932038930dba48c17e4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787515"
---
# <a name="gpu-activity-other-processes"></a>GPU 活動 (其他處理序)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[並行視覺化檢視] 中 [執行緒] 檢視的 [GPU 活動 (其他處理序)] 區段表示 GPU 代替系統中其他處理序處理要求的時間。 這些要求會以直接記憶體存取 (DMA) 封包格式傳送至 GPU。  區段的長度表示 GPU 處理封包的持續時間。  
  
 當您選取這種區段時，[目前] 索引標籤上的報告會顯示已處理封包的相關資訊。  此資訊包括封包在與 DirectX 引擎相關聯的硬體佇列中等候的時間量、送出封包的處理序和處理封包所需的時間。
