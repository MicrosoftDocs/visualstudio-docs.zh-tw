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
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810346"
---
# <a name="simplify-conditional-expression-refactoring"></a>簡化條件運算式重構

此重構適用於：

- C#

事項 **：** 可讓您簡化[條件運算式](/dotnet/csharp/language-reference/operators/conditional-operator)。

時機 **：** 您想要移除不必要的程式碼，以提供更清楚的說明。

**原因：** 簡化條件運算式可提供更清楚且更簡潔的語法。 此重構工具將會自動執行工作，而不需要手動執行。

## <a name="how-to"></a>使用方法

1. 將您的插入號放在條件運算式：

2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。

3. 選取 [**簡化條件運算式**]

    ![簡化條件運算式](media/simplify-conditional-expression.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)