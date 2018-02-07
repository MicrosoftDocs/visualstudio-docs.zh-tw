---
title: "產生建構函式 - 程式碼產生 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 891a33b74927d45434c4614dc4c5d7f1533ba4c0
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-constructor-in-visual-basic"></a>使用 Visual Basic 來產生建構函式
**功能：**讓您立即針對類別產生新建構函式的程式碼。 

**時機：** 您引進新的建構函式，並想要自動正確地宣告它。  

**原因：**您可以在使用建構函式之前先宣告它，不過，此功能將可自動搭配正確的參數來產生建構函式。 

**做法：**

1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的建構函式。

   ![醒目標示的程式碼](media/constructor-highlight-vb.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [在 '*TypeName*' 中產生建構函式]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [在 '*TypeName*' 中產生建構函式]。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-vb.png) 圖示。
     * 按一下 ![燈泡](media/bulb-vb.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「產生建構函式」預覽](media/constructor-preview-vb.png)

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 系統將會使用從建構函式使用方式推斷的任何參數來自動建立建構函式。

   ![「產生建構函式」結果](media/constructor-result-vb.png)
 
## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)