---
title: "產生欄位、屬性或區域變數 - 程式碼產生 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 766311f0ba165c87e61bb873baa3ab2f0b2d1402
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>使用 Visual Basic 來產生欄位、屬性或區域變數
**功能：**讓您針對先前未宣告的欄位、屬性或區域變數立即產生程式碼。 

**時機：** 您在輸入時引進新的欄位、屬性或區域變數，並想要自動正確地宣告這些項目。  

**原因：**您可以在使用欄位、屬性或區域變數之前先宣告這些項目，不過，此功能將可自動產生宣告和類型。 

**做法：**

1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的欄位、區域變數或屬性。

   ![醒目標示的程式碼](media/field-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生變數 '*Name*'] > [產生欄位/屬性/區域變數]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生變數 '*Name*'] > [產生欄位/屬性/區域變數]。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-vb.png) 圖示。
     * 按一下 ![燈泡](media/bulb-vb.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「產生欄位/屬性/區域變數」預覽](media/field-preview-vb.png)

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 系統將會使用從欄位、屬性或區域變數使用方式推斷的類型來自動建立這些項目。

   ![「產生欄位/屬性/區域變數」結果](media/field-result-vb.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)