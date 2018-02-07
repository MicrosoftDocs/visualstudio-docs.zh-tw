---
title: "使用 Visual Basic 以暫存變數的值來取代暫存變數 | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>使用 Visual Basic 來內嵌暫存變數

**功能：**讓您移除暫存變數，並改以其值來取代它。

**時機：**使用暫存變數會讓程式碼變得更難理解。

**原因：**移除暫存變數可讓程式碼變得較容易閱讀。

**做法：**

1. 醒目標示要內嵌的暫存變數，或將文字游標放在要內嵌的暫存變數內：

   ![醒目標示的程式碼](media/inline-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表。
   * **滑鼠**
     * 在程式碼上按一下滑鼠右鍵，選取 [快速動作與重構] 功能表。

1. 從 [預覽] 快顯視窗中選取 [內嵌暫存變數]。

   系統將會立即移除變數，並以變數的值取代使用該變數的地方。

   ![內嵌結果](media/inline-result-vb.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)