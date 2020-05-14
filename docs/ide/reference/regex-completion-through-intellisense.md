---
title: 透過 IntelliSense 功能表完成 RegEx
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
ms.openlocfilehash: 68b5cb480184a287d9fcb088b0a74ac9d607f3f2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093853"
---
# <a name="regex-completion-through-intellisense-menu"></a>透過 IntelliSense 功能表完成 RegEx

此重構適用於：

- C#

- Visual Basic

**內容：** 通過 IntelliSense 功能表完成正則運算式 （RegEx）。

**何時：** 您希望在 IntelliSense 的説明下編寫正則運算式。 IntelliSense 會提供基本的完成功能，並說明每個 RegEx 字元所代表的意義。 

**原因：** 編寫正則運算式是硬的，IntelliSense 可以説明你寫它。

## <a name="how-to"></a>操作方式

1. 將游標放在 RegEx 字串中。
2. 按**Ctrl**+**空間**可觸發 **"感知"** 功能表。
3. 選取想要新增至 RegEx 字串的字元。

   ![Regex 完成 IntelliSense](../media/regex-completion-intellisense.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
