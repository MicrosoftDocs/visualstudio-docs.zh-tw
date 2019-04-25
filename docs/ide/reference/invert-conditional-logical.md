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
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422207"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>反轉條件運算式和條件式 AND/OR 運算子

此重構適用於：

- C#
- Visual Basic

**功能：** 可讓您反轉條件運算式或條件式 AND/OR 運算子。

**時機：** 您擁有條件運算式或條件式 AND/OR 運算子，若反轉後會更容易了解。

**原因：** 以手動方式反轉運算式或條件式 AND/OR 運算子可能會花更長時間，並可能會產生錯誤。 此程式碼修正程式可協助您自動執行此重構。

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>反轉條件運算式和條件式 AND/OR 運算子重構

1. 將您的游標放在條件運算式或條件式 AND/OR 運算子中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
3. 選取 [反轉條件] 或**以 '||' 取代 '&&'**

    ![反轉條件](media/invert-conditional.png)

    ![反轉條件](media/invert-logical-operator.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
- [.NET 開發人員的秘訣](../../ide/visual-studio-2017-for-dotnet-developers.md)
