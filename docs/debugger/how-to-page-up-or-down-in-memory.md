---
title: HOW TO：Page Up 或在記憶體中的向下 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8452100eb744d019c0f4c8d5e62566ac761210
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894017"
---
# <a name="how-to-page-up-or-down-in-memory"></a>HOW TO：在記憶體中向上或向下翻頁

當您在 [記憶體] 視窗或 [反組譯碼] 視窗中檢視記憶體內容時，可以使用垂直捲軸在記憶體空間中上下移動。

### <a name="to-page-up-or-down-in-memory"></a>若要在記憶體中向上或向下翻頁

1. 若要向下翻頁 (移至較高的記憶體位址)，請按一下捲動方塊下方的垂直捲軸。

2. 若要向上翻頁 (移至較低的記憶體位址)，請按一下拇指上方的垂直捲軸。

   您也會發現垂直捲軸的操作方式沒有一定的標準。 現代電腦的位址空間很大，如果您抓取捲軸拇指並將它拖曳到隨機位置，很容易會遺失。 因此，拇指是「彈性載入」而且一定在捲軸的中央。 在機器碼應用程式中，您可以向上或向下翻頁，但不能自由捲動。

   在 Managed 應用程式中時，反組譯碼只有一個函式，您可以正常捲動。

   您會發現較高的位址出現在視窗底端。 若要檢視較高的位址，就必須向下而非向上移動。

#### <a name="to-move-up-or-down-one-instruction"></a>若要向上或向下移動一個指令

- 請按一下垂直捲軸頂端或底端的箭頭。

## <a name="see-also"></a>另請參閱
- [記憶體視窗](../debugger/memory-windows.md)
- [如何：使用反組譯碼視窗](../debugger/how-to-use-the-disassembly-window.md)
- [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)