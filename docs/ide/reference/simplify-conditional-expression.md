---
title: 簡化條件運算式
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290177"
---
# <a name="simplify-conditional-expression-refactoring"></a>簡化條件運算式重構

此重構適用於：

- C#

**功能：** 可讓您簡化[條件運算式](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)。

時機 **：** 您想要移除不必要的程式碼，以提供更清楚的資訊。

**原因：** 簡化條件運算式可以提供更清楚易懂且更簡潔的語法。 這個重構工具會自動執行工作，而不需要手動執行。

## <a name="how-to"></a>操作方式

1. 將插入號放在條件運算式上：

2. 按**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

3. 選取 [**簡化條件運算式**]

    ![簡化條件運算式](media/simplify-conditional-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)