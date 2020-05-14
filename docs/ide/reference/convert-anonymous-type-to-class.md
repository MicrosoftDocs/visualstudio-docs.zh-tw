---
title: 將匿名型別轉換為類別
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
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094284"
---
# <a name="convert-anonymous-type-to-class"></a>將匿名型別轉換為類別

此重構適用於：

- C#

- Visual Basic

**內容：** 將匿名型別轉換為類。

**何時：** 您有一個要在類中繼續構建的匿名型別。

**原因：** 如果您僅在本地使用它們，則匿名型別非常有用。 隨著您的程式碼增加，輕鬆地將其升階至類別會很有幫助。

## <a name="how-to"></a>操作方式

1. 將游標放在匿名型別中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

   ![將匿名型別轉換為類別](media/convert-anon-to-class.png)

2. 按 **Enter** 鍵接受重構。

   ![已接受將匿名型別轉換為類別](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
