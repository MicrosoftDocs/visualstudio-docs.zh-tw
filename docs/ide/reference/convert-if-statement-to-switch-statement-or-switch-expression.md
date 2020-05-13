---
title: 將 if 陳述式轉換為 switch 陳述式或 switch 運算式
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094144"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>將 if 陳述式轉換為 switch 陳述式或 switch 運算式

此重構適用於：

- C#

**內容：** 將 if 語句轉換為[switch 語句](/dotnet/csharp/language-reference/keywords/switch)或 C# 8.0[開關運算式](/dotnet/csharp/whats-new/csharp-8#switch-expressions)。

**何時：** 您希望將語句`if`轉換為`switch`語句或運算式，`switch`反之亦然。 

**原因：** 如果使用語句`if`，則此重構可以輕鬆轉換為`switch`語句或`switch`運算式。

## <a name="how-to"></a>操作方式

1. 將游標放在 `if` 關鍵字中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 從以下兩個選項中進行選擇： 

    選擇 **"轉換為"切換"語句**。

   ![將 if 語句轉換為切換語句](media/convert-if-to-switch-statement.png) 

    選擇 **"轉換為"開關"運算式**。 

    ![將 if 語句轉換為切換運算式](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
