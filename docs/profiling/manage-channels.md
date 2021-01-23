---
title: 管理通道 | Microsoft Docs
description: 瞭解如何為您的流程組織通道，讓您可以在並行視覺化程式的 [執行緒] 視圖中檢查特定模式。
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0dd8643f63a7a3e67400f09f00b999fff33f09e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721264"
---
# <a name="manage-channels"></a>管理通道
在並行視覺化檢視的 [執行緒檢視] 中，您可以針對處理序組織通道，以檢查特定模式。 您可以排序、上下移動及隱藏或顯示通道。

## <a name="sort-by"></a>排序依據
 您可以就目前的縮放層級，使用 [排序依據] 控制項來依據不同準則排序執行緒。 此方法對於尋找特定模式非常有幫助。 您可以根據這些準則來排序：

|準則|定義|
|--------------|----------------|
|開始時間|依據開始時間來排序執行緒。 這是預設的排序順序。|
|結束時間|依據結束時間來排序執行緒。|
|執行|依據執行時間花費百分比來排序執行緒。|
|同步處理|依據同步時間花費百分比來排序執行緒。|
|I/O|依據 I/O 時間花費百分比來排序執行緒。|
|睡眠|依據睡眠時間花費百分比來排序執行緒。|
|Paging|依據分頁時間花費百分比來排序執行緒。|
|先佔|依據先佔時間花費百分比來排序執行緒。|
|UI 處理|依據使用者介面處理時間花費百分比來排序執行緒。|

## <a name="move-selected-channel-up-or-down"></a>向上或向下移動選取的通道
 您可以使用這些控制項在清單中向上或向下移動通道。 例如，您可以將相關的通道放置在一起，以便檢查特定模式或跨執行緒的關係。

## <a name="move-selected-channel-to-top-or-bottom"></a>將選取的通道移至頂端或底部
 您可以將選取的通道移動到清單的頂端或底部，以便檢查特定模式，或是在檢查的時候排除不相關的通道。

## <a name="hide-selected-channels"></a>隱藏選取的通道
 當您想要隱藏通道時，請選取此控制項。 例如，如果某個執行緒百分之百與您的受管理處理序同步，則您可以在分析其他執行緒的時候隱藏它。

> [!NOTE]
> 隱藏的執行緒不會顯示在作用中圖例和分析報表中的計算時間。

## <a name="show-all-channels"></a>顯示所有通道
 此控制項會在有一個以上的隱藏通道時顯示。 若選取它，所有隱藏的元素就都會顯示，並且再次回到計算時間。

## <a name="move-markers-to-top"></a>將標記移至頂端
 如果追蹤包含標記事件，則您可以使用此命令將標記通道移動到時間軸的頂端。 系統會保留他們的相對順序。

## <a name="group-markers-by-thread"></a>依據執行緒來分組標記
 如果追蹤包含標記事件，您就可以使用此命令將標記通道分組在產生標記事件的執行緒下方。  磁碟通道會移動到通道清單的最上方，而 GPU 通道會移動到最下方。

## <a name="see-also"></a>另請參閱
- [縮放控制項 (執行緒視圖) ](../profiling/zoom-control-threads-view.md)
- [開啟/關閉測量模式](../profiling/measure-mode-on-off.md)
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)