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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80375573"
---
# <a name="move-type-to-namespace"></a>將類型移至命名空間

此重構適用於：

- C#

事項 **：** 將類型移至命名空間。

時機 **：** 您想要將類型移到不同的命名空間或資料夾。 

**原因：** 您想要重構解決方案的元件，並快速地將類型移至不同的命名空間或資料夾。 

## <a name="how-to"></a>操作方式

1. 將游標放在類別名稱中。
2. 按下**Ctrl** + **。** 以觸發 [快速動作與重構]**** 功能表。
3. 選取 [移至命名空間]****。

   ![移至命名空間重構](media/move-to-namespace.png)

4. 在開啟的對話方塊中，選取類型移動後所在的目標命名空間。 

   ![選取一個命名空間對話方塊](media/select-target-namespace.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
