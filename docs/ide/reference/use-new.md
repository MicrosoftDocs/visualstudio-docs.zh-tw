---
title: 使用 new()
description: 瞭解如何 `new()` 在無法使用時使用 `var` 。
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 889be18ab342f515bf5add266088a7ee69c087c1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218070"
---
# <a name="use-new"></a>使用`new()`

這適用於：

- C#

事項 **：** 使用 `new()` 。

時機 **：** 您有一個無法使用的欄位， `var` 或是不使用的程式碼樣式喜好設定 `var` 。

**原因：** 因此，您不需要重複兩次型別，就可以撰寫重複的程式碼。

## <a name="how-to"></a>使用方法

1. 將您的插入號放在欄位宣告上。

2. 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。

3. 選取 [ **使用新的 ( ... )**]：

    ![使用 ' new ( ... ) '](media/use-new.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
