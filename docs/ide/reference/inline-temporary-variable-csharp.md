---
title: "使用 C# 以暫存變數的值來取代暫存變數 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>使用 C# 來內嵌暫存變數 #

**功能：**讓您移除暫存變數，並改以其值來取代它。

**時機：**使用暫存變數會讓程式碼變得更難理解。

**原因：**移除暫存變數可讓程式碼變得較容易閱讀。

**做法：**

1. 醒目標示要內嵌的暫存變數，或將文字游標放在要內嵌的暫存變數內：

   ![醒目標示的程式碼](media/inline-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表。
   * **滑鼠**
     * 在程式碼上按一下滑鼠右鍵，然後選取 [快速動作與重構] 功能表。

1. 從 [預覽] 快顯視窗中選取 [內嵌暫存變數]。

   系統將會立即移除變數，並以變數的值取代使用該變數的地方。

   ![內嵌結果](media/inline-result-cs.png)

## <a name="see-also"></a>另請參閱

[重構](../refactoring-in-visual-studio.md)