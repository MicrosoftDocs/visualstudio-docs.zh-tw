---
title: 將匿名型別轉換為類別
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f29e31fb87d8b18e7f5a46d16f90217ee08d51f6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154578"
---
# <a name="convert-anonymous-type-to-class"></a>將匿名型別轉換為類別

此重構適用於：

- C#

**功能：** 將匿名型別轉換為類別。

**時機：** 您有想要持續在類別中建置的匿名型別。

**原因：**如果您只是在程式碼中局部使用匿名型別，它們非常實用。隨著您的程式碼增加，輕鬆地將其升階至類別會很有幫助。

## <a name="how-to"></a>操作說明

1. 將游標放在匿名型別中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![將匿名型別轉換為類別](media/convert-anon-to-class.png)

2. 按 **Enter** 鍵接受重構。

   ![已接受將匿名型別轉換為類別](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
