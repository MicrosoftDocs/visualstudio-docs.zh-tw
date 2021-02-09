---
title: split/merge if 陳述式
description: 瞭解如何使用 [快速動作與重構] 功能表來分割或合併 if 語句。
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 30ec77382cf404bc74f2ff5fed71cff360b9f28e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893382"
---
# <a name="split-or-merge-if-statements"></a>split/merge if 陳述式

此重構適用於：

- C#

- Visual Basic

**何謂：** **Split 或** merge [if](/dotnet/csharp/language-reference/keywords/if-else) 語句。

時機 **：** 您想要將 `if` 使用或運算子的語句 `&&` 分割 `||` 成嵌套 `if` 語句，或將 `if` 語句與外部 `if` 語句合併。

**原因：** 這是樣式喜好設定的考慮。  

## <a name="how-to"></a>使用方法

如果想要分割 `if` 陳述式：

1. 將游標放在 `if` 陳述式的 `&&` 或 `||` 運算子旁邊。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

    ![分割 if 陳述式](../media/split-if-statement.png)

3. 選取 [分割成巢狀 if 陳述式]。

    ![分割 if 陳述式完成](../media/split-if-statement-complete.png)

如果您想要合併內部 `if` 陳述式與外部 `if` 陳述式： 

1. 將游標放在內部 `if` 關鍵字中。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

    ![合併 if 陳述式](../media/merge-if-statement.png)

3. 選取 [與外部 if 陳述式合併]。

    ![合併 If 陳述式完成](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)