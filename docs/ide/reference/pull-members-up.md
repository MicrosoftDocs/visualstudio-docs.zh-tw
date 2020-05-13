---
title: 向上提取成員
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969145"
---
# <a name="pull-members-up"></a>向上提取成員

此重構適用於：

- C#

- Visual Basic

**內容：** 允許您將成員拉到基類型。

**何時：** 您已經實現了一個介面，並且希望將成員移動到基本類型。

**原因：** 向上拉取成員使介面的其他實現也能夠繼承這些成員。

## <a name="how-to"></a>操作方式

1. 將游標放在實作介面的任何成員中。
2. 按**Ctrl**+**。** 以觸發 [快速動作與重構]**** 功能表。

   ![向上提取成員](media/pull-members-up.png)

2. 選取 [將成員向上提取到基底類型]****。

3. 在對話方塊中，選取您想要新增到所選介面的成員。

   ![向上提取成員](media/pull-members-up-dialog.png)

4. 選擇 **"確定**"。 選取的成員會向上提取到介面。

   ![向上提取成員已完成](media/pull-members-up-completed.png)

## <a name="see-also"></a>另請參閱

- [Refactoring](../refactoring-in-visual-studio.md)
