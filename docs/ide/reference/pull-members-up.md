---
title: 向上提取成員
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335792"
---
# <a name="pull-members-up"></a>向上提取成員

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您將成員向上提取到基底類型。

**時機：** 您已實作了介面，而且想要將成員移到基底類型。

**原因：** 向上提取成員讓您介面的其他實作也可繼承這些成員。

## <a name="how-to"></a>操作說明

1. 將游標放在實作介面的任何成員中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![向上提取成員](media/pull-members-up.png)

2. 選取 [將成員向上提取到基底類型]。

3. 在對話方塊中，選取您想要新增到所選介面的成員。

   ![向上提取成員](media/pull-members-up-dialog.png)

4. 選擇 [確定] 。 選取的成員會向上提取到介面。

   ![向上提取成員已完成](media/pull-members-up-completed.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
