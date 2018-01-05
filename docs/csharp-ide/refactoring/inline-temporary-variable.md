---
title: "內嵌暫存變數-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 0a2d04c6582153e75f28b970e90c3475e1affb65
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>使用 C# 內嵌暫存變數 #
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

## <a name="see-also"></a>請參閱  
[重構 (C#)](../refactoring-csharp.md)