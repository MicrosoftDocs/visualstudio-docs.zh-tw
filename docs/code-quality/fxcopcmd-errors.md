---
title: FxCopCmd 錯誤
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a40d4b7baa3d994ca41213a100881e5f509a5167
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948260"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd 工具錯誤

FxCopCmd 不會考慮所有的錯誤，是嚴重的錯誤。 如果 FxCopCmd 有足夠的資訊來執行部分的分析，它會執行分析和報告所發生的錯誤。 錯誤的程式碼，也就是 32 位元整數，包含對應至錯誤的數字值的位元組合。

下表描述 FxCopCmd 所傳回的錯誤碼：

|錯誤|數字值|
|-----------|-------------------|
|沒有錯誤|0x0|
|分析錯誤|0x1|
|規則的例外狀況|0x2|
|專案載入錯誤|0x4|
|組件載入錯誤|0x8|
|規則文件庫載入錯誤|0x10|
|匯入報表載入錯誤|0x20|
|輸出錯誤|0x40|
|命令列參數錯誤|0x80|
|初始化錯誤|0x100|
|組件參考錯誤|0x200|
|BuildBreakingMessage|0x400|
|未知的錯誤|0x1000000|

**分析錯誤**傳回嚴重錯誤。 表示無法完成分析。 適用時，錯誤程式碼也會包含嚴重錯誤的根本原因。 在下列情況會產生嚴重的錯誤：

- 無法執行分析，因為沒有足夠的輸入。

- 分析會擲回 FxCopCmd 未處理的例外狀況。

- 找不到指定的專案檔，或已損毀。

- 未指定輸出選項，或無法寫入檔案。

> [!NOTE]
> FxCopCmd 傳回碼**組件參考錯誤**0x200 本身是警告，而不是錯誤。 此傳回碼指出，那里遺漏間接參考，但該 FxCopCmd 無法處理它們。 警告表示，某些分析結果可能被盜用的可能性。 將視為**組件參考錯誤**為錯誤時它結合任何其他傳回碼。

## <a name="see-also"></a>另請參閱

- [程式碼分析應用程式錯誤](../code-quality/code-analysis-application-errors.md)