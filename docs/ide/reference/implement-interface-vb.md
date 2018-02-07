---
title: "實作介面 - 程式碼產生 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>使用 Visual Basic 來實作介面
**功能：**讓您立即產生實作介面所需的程式碼。 

**時機：**您想要從介面繼承。  

**原因：**您可以手動逐一實作所有介面，不過，此功能將可自動產生所有方法簽章。 

**做法：**

1. 將游標放在有紅色曲線的行上，該曲線代表您已參考介面，但尚未實作所有必要的成員。

   ![醒目標示的程式碼](media/interface-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [明確實作介面]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [明確實作介面]。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-vb.png) 圖示。
     * 按一下 ![燈泡](media/bulb-vb.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「實作類別」預覽](media/interface-preview-vb.png)

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。
   >
   >此外，您也可以使用位於預覽視窗底部的 [文件]、[專案] 及 [方案] 連結，在實作介面的多個類別上建立適當的方法簽章。

1. 系統將會自動建立介面的方法簽章，並備妥以供實作。

   ![「實作類別」結果](media/interface-result-vb.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)