---
title: 目前索引標籤 | Microsoft Docs
description: 選取 [執行緒] 視圖的目前索引標籤，以查看 CPU 執行緒區段或封鎖區段的呼叫堆疊。 此外，也有 DirectX 區段的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65261d6304ead5ade7c28f40495fa68afb0c2171
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686209"
---
# <a name="current-tab"></a>目前索引標籤
按一下 [目前] 索引標籤，如果選取 CPU 執行緒區段，您可以查看時間軸中最接近目前選取點的呼叫堆疊 (如果有)。  此時，選取點會以黑色箭號或插入號顯示在時間軸上方。 選取封鎖的區段之後，因為沒有任何執行，所以不會顯示插入號。 不過，仍然會反白顯示區段，而且會顯示呼叫堆疊。

 [目前] 索引標籤也會顯示 DirectX 活動區段、標記和 I/O 存取的相關資訊。  對於 DirectX 活動區段，會顯示硬體佇列處理 DMA 封包方式的相關資訊。  對於標記，會顯示描述和標記類型的相關資訊。  對於 I/O 存取，會顯示讀取或寫入的檔案和位元組數目的相關資訊。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)