---
title: 使用 new()
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a129e94f6009eec51995b6a4e170f0a804e6407f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889807"
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
