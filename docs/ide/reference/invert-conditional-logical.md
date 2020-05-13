---
title: 轉換條件運算式和邏輯運算
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
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531681"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>反轉條件運算式和條件式 AND/OR 運算子

此重構適用於：

- C#
- Visual Basic

**內容：** 允許您反轉條件運算式或條件 AND/OR 運算子。

**何時：** 您有一個條件運算式或條件 AND/OR 運算子，如果反轉，將更好地理解該運算子。

**原因：** 手動反轉運算式或條件 AND/OR 運算子可能需要更長的時間，並可能導致錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>反轉條件運算式和條件式 AND/OR 運算子重構

1. 將您的游標放在條件運算式或條件式 AND/OR 運算子中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [反轉條件]**** 或**以 '||' 取代 '&&'**

    ![反轉條件](media/invert-conditional.png)

    ![反轉條件](media/invert-logical-operator.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
