---
title: "產生的建構函式的程式碼產生 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0380076319a80ba85aa59c388959baece9008e94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-visual-basic"></a>在 Visual Basic 中產生的建構函式
**項目：**可讓您立即產生新的建構函式，在類別上的程式碼。 

**當：**您引入新的建構函式，而且想要正確地自動宣告。  

**原因：**不過這項功能將它，以適當的參數自動產生，您可以再使用它，宣告建構函式。 

**如何：**

1. 將游標放在該行其中會有紅色曲線，表示您已使用建構函式不存在。

   ![反白顯示的程式碼](media/constructor_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**中的產生建構函式 '*TypeName*' * * 從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**中的產生建構函式 '*TypeName*' * * 從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![產生建構函式預覽](media/constructor_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。

1. 建構函式會自動建立的任何參數，從其使用方式推斷。

   ![產生建構函式的結果](media/constructor_result.png)
  
## <a name="see-also"></a>另請參閱  
[程式碼產生 (Visual Basic)](../code-generation-vb.md)  
[預覽變更](../../ide/preview-changes.md)