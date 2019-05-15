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
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531594"
---
# <a name="invert-if-statement"></a>反轉 if 陳述式

此重構適用於：

- C#
- Visual Basic

**功能：** 可讓您反轉 `if` 或 `if else` 陳述式，而不需要變更程式碼的意義。

**時機：** 當您擁有反轉後會更容易了解的 `if` 或 `if else` 陳述式時。

**原因：** 以手動方式反轉 `if` 或 `if else` 陳述式可能會花更長時間，且可能會產生錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-if-statement-refactoring"></a>反轉 if 陳述式重構

1. 將游標放在 `if` 或 `if else` 陳述式中。

    ![反轉 if else](media/invert-if.png)

2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

    ![反轉 if else 程式碼修正](media/invert-if-codefix.png)

3. 選取 [反轉 if]。

    ![反轉 if else 結果](media/invert-if-codefix-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的秘訣](../csharp-developer-productivity.md)
