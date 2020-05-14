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
monikerRange: vs-2019
ms.openlocfilehash: 58d2757fa8798b67c8e597f5f82bc65a279f4a90
ms.sourcegitcommit: 8ff6c6975148ce43bdac21c8995fbab910c312fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2020
ms.locfileid: "80375573"
---
# <a name="move-type-to-namespace"></a>將類型移至命名空間

此重構適用於：

- C#

**內容：** 將類型移動到命名空間。

**何時：** 您希望將類型移動到其他命名空間或資料夾。 

**原因：** 您希望重構解決方案的某些部分，並快速將類型移動到其他命名空間或資料夾。 

## <a name="how-to"></a>操作方式

1. 將游標放在類別名稱中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [移至命名空間]****。

   ![移至命名空間重構](media/move-to-namespace.png)

4. 在開啟的對話方塊中，選取類型移動後所在的目標命名空間。 

   ![選取一個命名空間對話方塊](media/select-target-namespace.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
