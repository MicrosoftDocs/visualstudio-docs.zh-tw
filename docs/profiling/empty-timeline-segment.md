---
title: 空白時間表區段 | Microsoft Docs
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
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970105"
---
# <a name="empty-timeline-segment"></a>空白時間表區段
在並行視覺化檢視中，時間表區段空白 (具有白色背景) 的原因取決於通道的類型。

- 如為 CPU 執行緒通道，表示執行緒在時間表的這個部分不存在。 如果您對執行緒感興趣，您可以使用縮放控制項或水平捲動來尋找其執行區段。

- 如為 I/O 通道，表示該時間點沒有代表目標處理序的磁碟存取發生。

- 如為 DirectX 通道，表示在時間表的這個部分沒有代表目標處理序執行的 GPU 工作。

- 如為標記通道，表示未產生任何標記。

## <a name="see-also"></a>另請參閱
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)
- [縮放控制 (執行緒檢視)](../profiling/zoom-control-threads-view.md)