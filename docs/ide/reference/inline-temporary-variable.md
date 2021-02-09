---
title: 以暫存變數的值來取代暫存變數
description: 瞭解如何使用 [快速動作與重構] 功能表來移除暫存變數，並改為以其值取代。
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ebe062d5dd569ae1d2162ea7334f91d8b82decdb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852371"
---
# <a name="inline-a-temporary-variable-refactoring"></a>內嵌暫存變數重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您移除暫存變數，並改以其值來取代它。

**時機：** 使用暫存變數會讓程式碼變得更難理解。

**原因：** 移除暫存變數可讓程式碼變得較容易閱讀。

## <a name="how-to"></a>使用方法

1. 醒目標示要內嵌的暫存變數，或將文字游標放在要內嵌的暫存變數內：

   - C#：

       ![醒目提示的程式碼 - C#](media/inline-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/inline-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 按下 **Ctrl** + **。** 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，然後選取 [快速動作與重構] 功能表。

3. 從 [預覽] 快顯視窗中選取 [內嵌暫存變數]。

   系統會移除變數，並以變數的值取代使用該變數的地方。

   - C#：

      ![內嵌結果 - C#](media/inline-result-cs.png)

   - Visual Basic：

      ![內嵌結果 - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)
