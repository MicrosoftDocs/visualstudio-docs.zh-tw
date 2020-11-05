---
title: '使用新的 ( # A1'
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b2091c046efac9f5676e5d2d99ef798283b95f6e
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402281"
---
# <a name="use-new"></a>使用`new()`

這適用於：

- C#

事項 **：** 使用 `new()` 。

時機 **：** 您有一個無法使用的欄位， `var` 或是不使用的程式碼樣式喜好設定 `var` 。

**原因：** 因此，您不需要重複兩次型別，就可以撰寫重複的程式碼。

## <a name="how-to"></a>操作方式

1. 將您的插入號放在欄位宣告上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取 [ **使用新的 ( ... )** ]：

    ![使用 ' new ( ... ) '](media/use-new.png)

## <a name="see-also"></a>請參閱

- [重構](../refactoring-in-visual-studio.md)
