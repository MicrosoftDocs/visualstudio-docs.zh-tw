---
title: 將 if 語句轉換成 switch 語句或 switch 運算式
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280779"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>將 if 語句轉換成 switch 語句或 switch 運算式

此重構適用於：

- C#

**功能：** 將 if 語句轉換成[switch 語句](/dotnet/csharp/language-reference/keywords/switch)或C# 8.0 [switch 運算式](/dotnet/csharp/whats-new/csharp-8#switch-expressions)。

時機 **：** 您想要將 `if` 語句轉換成 `switch` 語句或 `switch` 運算式，反之亦然。 

**原因：** 如果您使用 `if` 語句，則此重整功能可讓您輕鬆地轉換成 `switch` 的語句或 `switch` 運算式。

## <a name="how-to"></a>操作方式

1. 將游標放在 `if` 關鍵字中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構] 功能表。
3. 選取 [**轉換成 ' switch ' 語句**]。

   ![將 if 語句轉換成 switch 語句或 switch 運算式](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
