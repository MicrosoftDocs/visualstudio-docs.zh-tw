---
title: 反轉 if 陳述式
description: 瞭解如何使用 [快速動作] 和 [重構] 功能表來反轉 if 或 else 語句，而不變更程式碼的意義。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616976"
---
# <a name="invert-if-statement"></a>反轉 if 陳述式

此重構適用於：

- C#
- Visual Basic

事項 **：** 可讓您反轉 `if` 或 `if else` 語句，而不會變更程式碼的意義。

時機 **：** 當您有一個 `if` 或多個 `if else` 語句時，會更清楚地瞭解反向。

**原因：** 以 `if` `if else` 手動方式反轉或語句可能需要更長的時間，而且可能會導致錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-if-statement-refactoring"></a>反轉 if 陳述式重構

1. 將游標放在 `if` 或 `if else` 陳述式中。

    ![反轉 if else](media/invert-if.png)

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

    ![反轉 if else 程式碼修正](media/invert-if-codefix.png)

3. 選取 [反轉 if]。

    ![反轉 if else 結果](media/invert-if-codefix-result.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
