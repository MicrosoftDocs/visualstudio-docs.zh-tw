---
title: split/merge if 陳述式
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093688"
---
# <a name="split-or-merge-if-statements"></a>split/merge if 陳述式

此重構適用於：

- C#

- Visual Basic

**內容：****拆分**或合併[（如果](/dotnet/csharp/language-reference/keywords/if-else)語句）。

**何時：** 您希望將使用`if``&&`或`||`運算子的語句拆分為嵌套`if`語句，或將`if`語句與外部`if`語句合併。

**原因：** 這是一個風格偏好的問題。  

## <a name="how-to"></a>操作方式

如果想要分割 `if` 陳述式：

1. 將游標放在 `if` 陳述式的 `&&` 或 `||` 運算子旁邊。

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

    ![分割 if 陳述式](../media/split-if-statement.png)

3. 選取 [分割成巢狀 if 陳述式]****。

    ![分割 if 陳述式完成](../media/split-if-statement-complete.png)

如果您想要合併內部 `if` 陳述式與外部 `if` 陳述式： 

1. 將游標放在內部 `if` 關鍵字中。

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

    ![合併 if 陳述式](../media/merge-if-statement.png)

3. 選取 [與外部 if 陳述式合併]****。

    ![合併 If 陳述式完成](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)