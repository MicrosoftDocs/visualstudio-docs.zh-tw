---
title: 空白時間表區段 | Microsoft Docs
description: 在 Visual Studio 並行視覺化檢視器中，瞭解時間軸區段可能是空的， (具有某種通道的白色背景) 。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15dc4526ce101e21c00fe083b85f81db92bcd609
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801425"
---
# <a name="empty-timeline-segment"></a>空白時間表區段
在並行視覺化檢視中，時間表區段空白 (具有白色背景) 的原因取決於通道的類型。

- 如為 CPU 執行緒通道，表示執行緒在時間表的這個部分不存在。 如果您對執行緒感興趣，您可以使用縮放控制項或水平捲動來尋找其執行區段。

- 如為 I/O 通道，表示該時間點沒有代表目標處理序的磁碟存取發生。

- 如為 DirectX 通道，表示在時間表的這個部分沒有代表目標處理序執行的 GPU 工作。

- 如為標記通道，表示未產生任何標記。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)
- [縮放控制項 (執行緒視圖) ](../profiling/zoom-control-threads-view.md)