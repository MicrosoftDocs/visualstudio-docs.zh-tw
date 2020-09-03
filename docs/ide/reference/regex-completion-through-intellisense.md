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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093853"
---
# <a name="regex-completion-through-intellisense-menu"></a>透過 IntelliSense 功能表完成 RegEx

此重構適用於：

- C#

- Visual Basic

事項 **：** 正則運算式 (RegEx) 透過 IntelliSense 功能表完成。

時機 **：** 您想要使用 IntelliSense 的說明來撰寫正則運算式。 IntelliSense 會提供基本的完成功能，並說明每個 RegEx 字元所代表的意義。 

**原因：** 撰寫 RegEx 很困難，而 IntelliSense 可協助您撰寫。

## <a name="how-to"></a>操作方式

1. 將游標放在 RegEx 字串中。
2. 按**Ctrl** + **空格鍵**以觸發 [ **IntelliSense** ] 功能表。
3. 選取想要新增至 RegEx 字串的字元。

   ![Regex 完成 IntelliSense](../media/regex-completion-intellisense.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
