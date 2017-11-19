---
title: "內嵌暫存變數重構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a63d6407-5acb-4d5f-8c0e-ecedddc07177
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 574a1a41464ede08571e1c0201618d666fa7ad92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>內嵌在 Visual Basic 中的暫存變數
**項目：**可讓您移除使用的暫存變數，並取代的實際程式碼。

**當：**的暫存變數使用，讓程式碼更難了解。  

**原因：**移除暫存變數可能會讓程式碼更容易閱讀，在某些情況下

**如何：**

1. 反白顯示，或將文字指標放置要內嵌之暫存變數：

   ![反白顯示的程式碼](media/inline_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**內嵌暫存變數**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**內嵌暫存變數**從預覽視窗快顯視窗。

   變數將會移除，而且其使用方式由變數的值取代。

   ![Inline 結果](media/inline_result.png)

## <a name="see-also"></a>另請參閱
[重構 (Visual Basic)](../refactoring-vb.md)