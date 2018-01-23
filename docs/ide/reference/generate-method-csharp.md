---
title: "產生方法 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e4caf80bec38305613111f290b80eafb74547598
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-method-in-c"></a>使用 C# 來產生方法 #
**功能：**讓您立即將方法新增至類別。 

**時機：** 您引進新的方法，並想要自動正確地宣告它。  

**原因：**您可以在使用方法和參數之前先宣告方法和參數，不過，此功能將可自動產生宣告。 

**做法：**

1. 將游標放在有紅色曲線的行上，該曲線代表您使用尚未存在的方法。

   ![醒目標示的程式碼](media/method-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生方法]。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [產生方法]。
     * 將游標暫留在紅色曲線上，然後按一下顯示的 ![燈泡](media/bulb-cs.png) 圖示。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「產生方法」預覽](media/method-preview-cs.png)

   >[!TIP]
   >請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 系統將會使用從方法使用方式推斷的任何參數來自動建立方法。

   ![「產生方法」結果](media/method-result-cs.png)

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)
