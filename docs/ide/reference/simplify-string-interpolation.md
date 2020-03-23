---
title: 簡化字串插補
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
ms.openlocfilehash: a8b0fd53164cb98921b111d49fa04a76c9d0d8a8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094304"
---
# <a name="simplify-string-interpolation-refactoring"></a>簡化字串插值重構

此重構適用於：

- C#

- Visual Basic

**內容：** 允許您簡化[字串插值](https://docs.microsoft.com/dotnet/csharp/tutorials/string-interpolation)。

**何時：** 您有一個可以簡化的字串插值。

**原因：** 簡化字串插值可以提供更清晰、更簡潔的語法。 此重構工具將自動執行任務，而不必手動執行。

## <a name="how-to"></a>操作方式

1. 將插入符放在字串插值上：

2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

3. 選擇 **"簡化插值"**

    ![簡化字串插補](media/simplify-string-interpolation.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)