---
title: 使參數換行、縮排及對齊
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
ms.openlocfilehash: 1490ff0bcae91a6f4870b0cfb623d975fa1e064b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335786"
---
# <a name="wrap-indent-and-align-parameters"></a>使參數換行、縮排及對齊

此重構適用於：

- C#

- Visual Basic

**功能：** 使參數換行、縮排及對齊。

**時機：** 您有具多個參數的方法宣告或呼叫。

**原因：** 當一長串參數依照使用者想要的方式換行或縮排後，閱讀起來會更加輕鬆。

## <a name="how-to"></a>操作說明

1. 將游標放在參數清單中。
2. 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。

   ![使參數換行、縮排及對齊](media/wrap-parameters.png)

3. 按 **Enter** 鍵接受重構。

   ![已套用使參數換行、縮排及對齊](media/wrap-parameters-completed.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
