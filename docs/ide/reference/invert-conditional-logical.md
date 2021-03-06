---
title: 轉換條件運算式和邏輯運算
description: 瞭解如何使用 [快速動作與重構] 功能表來反轉條件運算式或條件式 AND/OR 運算子。
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852241"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>反轉條件運算式和條件式 AND/OR 運算子

此重構適用於：

- C#
- Visual Basic

事項 **：** 讓您可以反轉條件運算式或條件式 AND/OR 運算子。

時機 **：** 您有條件運算式或條件式 AND/OR 運算子，如果反轉，則會更清楚瞭解。

**原因：** 以手動方式反轉運算式或條件式和/或運算子可能需要更長的時間，而且可能會導致錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>反轉條件運算式和條件式 AND/OR 運算子重構

1. 將您的游標放在條件運算式或條件式 AND/OR 運算子中。
2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
3. 選取 [反轉條件] 或 **以 '||' 取代 '&&'**

    ![[反向條件] 選項的螢幕擷取畫面。](media/invert-conditional.png)

    ![以 | | 取代 && 的螢幕擷取畫面選項。](media/invert-logical-operator.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的祕訣](../csharp-developer-productivity.md)
