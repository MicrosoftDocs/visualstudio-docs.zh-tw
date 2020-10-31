---
title: 將 if 語句轉換成 switch 語句或運算式
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8e093325ff4a4e6a9f8a2623e7e42f69bb6fa62f
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102528"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>將 if 陳述式轉換為 switch 陳述式或 switch 運算式

此重構適用於：

- C#

事項 **：** 將 if 語句轉換成 [switch 語句](/dotnet/csharp/language-reference/keywords/switch)或 c # 8.0 [switch 運算式](/dotnet/csharp/whats-new/csharp-8#switch-expressions)。

時機 **：** 您想要將 `if` 語句轉換成 `switch` 語句或 `switch` 運算式，反之亦然。

**原因：** 如果您使用的是 `if` 語句，這種重整功能可讓您輕鬆地轉換成 `switch` 語句或 `switch` 運算式。

## <a name="how-to"></a>使用方法

1. 將游標放在 `if` 關鍵字中。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構]  功能表。
3. 從下列兩個選項中選取：

    選取 [ **轉換成 ' switch ' 語句** ]。

   ![將 if 語句轉換為 switch 語句](media/convert-if-to-switch-statement.png)

    選取 [ **轉換成 ' switch ' 運算式** ]。

    ![將 if 語句轉換為 switch 運算式](media/convert-if-to-switch-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
