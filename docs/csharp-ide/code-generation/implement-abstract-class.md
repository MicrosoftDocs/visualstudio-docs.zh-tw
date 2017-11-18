---
title: "實作抽象類別的程式碼產生 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 301c4f7a8955f22952787c78eaeabff826495c29
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="implement-an-abstract-class-in-c"></a>在 C# 中實作的抽象類別 #
**項目：**可讓您立即產生來實作抽象類別的程式碼。 

**當：**您想要繼承自抽象類別。  

**原因：**不過這項功能會自動產生所有的方法簽章，您可以手動實作所有抽象成員的其中一個。 

**如何：**

1. 將游標放在該行其中會有紅色曲線，表示您必須繼承自抽象類別，但未實作所有必要的成員。

   ![反白顯示的程式碼](media/abstract_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**實作抽象類別**從預覽視窗快顯視窗。
   * **滑鼠**
     * 以滑鼠右鍵按一下並選取**快速控制項目及重構**功能表，然後選取**實作抽象類別**從預覽視窗快顯視窗。
     * 將滑鼠停留在紅色波浪線，然後按一下 ![Lightbulb](media/bulb.png) 圖示會出現。
     * 按一下 ![Lightbulb](media/bulb.png) 如果文字資料指標已經存在於紅色曲線的線條，會出現在左邊界的圖示。

   ![實作類別預覽](media/abstract_preview.png)

   >[!TIP]
   >使用[**預覽變更**](../../ide/preview-changes.md)若要查看的所有變更都會在您的選取項目之前，[預覽] 視窗底部的連結。
   >
   >此外，您可以使用**文件**，**專案**，和**方案**建立跨多個適當的方法簽章的 [預覽] 視窗底部的連結繼承自抽象類別的類別。

1. 抽象方法簽章將會自動建立，以便實作。

   ![實作類別結果](media/abstract_result.png)

## <a name="see-also"></a>另請參閱  
[程式碼產生 (C#)](../code-generation-csharp.md)  
[預覽變更](../../ide/preview-changes.md)
