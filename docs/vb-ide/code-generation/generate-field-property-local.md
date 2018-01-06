---
title: "產生欄位、 屬性或本機-產生程式碼 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e23dfa2b482a16d70ef71614ba35f9b20523aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>產生 Visual Basic 中的欄位、 屬性或本機
**項目：**可讓您立即產生先前未宣告的欄位、 屬性或本機的程式碼。 

**當：**您引入新的欄位、 屬性或本機打字時，而且想要正確地自動宣告。  

**原因：**您無法再使用它，不過這項功能將會產生宣告，並輸入自動宣告欄位、 屬性或本機。 

**如何：**

1. 將游標放在該行是紅色波浪線，表示您已經使用本機的欄位或屬性不存在。

   ![反白顯示的程式碼](media/field_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**產生變數 '*名稱*' > 產生欄位/屬性/本機 * * 從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**產生變數 '*名稱*' > 產生欄位/屬性/本機 * * 從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![產生欄位/屬性/本機預覽](media/field_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 欄位、 屬性或本機將會以自動建立從其使用方式推斷的型別。

   ![產生欄位/屬性/本機結果](media/field_result.png)

## <a name="see-also"></a>請參閱  
[程式碼產生 (Visual Basic)](../code-generation-vb.md)  
[預覽變更](../../ide/preview-changes.md)