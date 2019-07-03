---
title: split/merge if 陳述式
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160734"
---
# <a name="split-or-merge-if-statements"></a>split/merge if 陳述式

此重構適用於：

- C#

**功能：** **功能：** 分割或合併 [if](/dotnet/csharp/language-reference/keywords/if-else) 陳述式。

**時機：** 如果想要將使用 `&&` 或 `||` 運算子的 `if` 分割為巢狀 `if` 陳述式，或合併一個 `if` 陳述式與一個外部 `if` 陳述式。

**原因：** 這主要是樣式偏好問題。  

## <a name="how-to"></a>操作說明

如果想要分割 `if` 陳述式：

1. 將游標放在 `if` 陳述式的 `&&` 或 `||` 運算子旁邊。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構]  功能表。

    ![分割 if 陳述式](../media/split-if-statement.png)

3. 選取 [分割成巢狀 if 陳述式]  。

    ![分割 if 陳述式完成](../media/split-if-statement-complete.png)

如果您想要合併內部 `if` 陳述式與外部 `if` 陳述式： 

1. 將游標放在內部 `if` 關鍵字中。

2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構]  功能表。

    ![合併 if 陳述式](../media/merge-if-statement.png)

3. 選取 [與外部 if 陳述式合併]  。

    ![合併 If 陳述式完成](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)