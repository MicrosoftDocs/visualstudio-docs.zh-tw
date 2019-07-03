---
title: 將類型移至命名空間
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 821e915a0b66f25c5b89a83b31e93b01aea6f400
ms.sourcegitcommit: b593bb889f049fcbdff502c30b73178ed17dbdf0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67292704"
---
# <a name="move-type-to-namespace"></a>將類型移至命名空間

此重構適用於：

- C#

**功能：** 將類型移至命名空間。

**時機：** 您想要將類型移到不同的命名空間或資料夾。 

**原因：** 您想要重構解決方案的組件，並希望能快速地將類型移到不同的命名空間或資料夾。 

## <a name="how-to"></a>操作說明

1. 將游標放在類別名稱中。
2. 在字行任何地方按 **Ctrl**+ **.** ， 以觸發 [快速動作與重構]  功能表。
3. 選取 [移至命名空間]  。

   ![移至命名空間重構](media/move-to-namespace.png)

4. 在開啟的對話方塊中，選取類型移動後所在的目標命名空間。 

   ![選取一個命名空間對話方塊](media/select-target-namespace.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
