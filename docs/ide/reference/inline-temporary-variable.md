---
title: 以暫存變數的值來取代暫存變數
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6fea50f3cceb907cb014d29bb46988ab07dad6c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066859"
---
# <a name="inline-a-temporary-variable-refactoring"></a>內嵌暫存變數重構

此重構適用於：

- C#

- Visual Basic

**功能：** 讓您移除暫存變數，並改以其值來取代它。

**時機：** 使用暫存變數會讓程式碼變得更難理解。

**原因：** 移除暫存變數可讓程式碼變得較容易閱讀。

## <a name="how-to"></a>操作說明

1. 醒目標示要內嵌的暫存變數，或將文字游標放在要內嵌的暫存變數內：

   - C#: 

       ![醒目提示的程式碼 - C#](media/inline-highlight-cs.png)

   - Visual Basic：

       ![醒目提示的程式碼 - Visual Basic](media/inline-highlight-vb.png)

2. 接著，執行下列其中一項操作：

   - **鍵盤**
      - 在字行任何地方按 **Ctrl**+**.**， 以觸發 [快速動作與重構] 功能表。
   - **滑鼠**
      - 在程式碼上按一下滑鼠右鍵，然後選取 [快速動作與重構] 功能表。

3. 從 [預覽] 快顯視窗中選取 [內嵌暫存變數]。

   系統會移除變數，並以變數的值取代使用該變數的地方。

   - C#: 

      ![內嵌結果 - C#](media/inline-result-cs.png)

   - Visual Basic：

      ![內嵌結果 - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>另請參閱

- [重構](../refactoring-in-visual-studio.md)