---
title: 反轉 if 陳述式
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531594"
---
# <a name="invert-if-statement"></a>反轉 if 陳述式

此重構適用於：

- C#
- Visual Basic

**內容：** 允許您在不更改代碼的含義`if`的情況下`if else`反轉 或 語句。

**何時：** 當您有一個`if``if else`或 語句，在反轉時會更好理解。

**原因：** 手動反轉`if`或`if else`語句可能需要更長的時間，並可能導致錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-if-statement-refactoring"></a>反轉 if 陳述式重構

1. 將游標放在 `if` 或 `if else` 陳述式中。

    ![反轉 if else](media/invert-if.png)

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

    ![反轉 if else 程式碼修正](media/invert-if-codefix.png)

3. 選取 [反轉 if]****。

    ![反轉 if else 結果](media/invert-if-codefix-result.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
