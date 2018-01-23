---
title: "引進區域變數 - 程式碼產生 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2018
---
# <a name="introduce-a-local-variable-in-c"></a>使用 C# 來引進區域參數 #

**功能：**讓您立即產生區域變數來取代現有的運算式。

**時機：**您有只要放在區域變數中便可在稍後輕鬆重複使用的程式碼。

**原因：**您可以多次複製和貼上程式碼以在各種位置中使用該程式碼，不過，最好是只執行該作業一次，將結果儲存在區域變數中，然後全程使用區域變數。

**做法：**

1. 醒目標示您想要指派給新區域變數的運算式。

   ![醒目標示的程式碼](media/local-highlight-cs.png)

1. 接著，執行下列其中一項操作：
   * **鍵盤**
     * 按 **Ctrl+.** 以觸發 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [為所有出現 '*expression*' 之處引進區域]，其中 *expression* 是您已醒目標示的程式碼。
   * **滑鼠**
     * 按一下滑鼠右鍵並選取 [快速動作與重構] 功能表，然後從 [預覽] 快顯視窗中選取 [為所有出現 '*expression*' 之處引進區域]，其中 *expression* 是您已醒目標示的程式碼。
     * 按一下 ![燈泡](media/bulb-cs.png) 圖示，如果文字游標已經在含有紅色曲線的行上，此圖示就會出現在左邊界上。

   ![「引進區域」預覽](media/local-preview-cs.png)

   > [!TIP]
   > 請使用位於預覽視窗底部的 [[預覽變更](../../ide/preview-changes.md)] 連結，以在進行選取之前先查看將進行的所有變更。

1. 系統將會使用從區域變數使用方式推斷的類型來自動建立區域變數。  輸入名稱來為新區域變數提供一個新名稱。

   ![「引進區域」結果](media/local-result-cs.png)

   > [!NOTE]
   > 您可以使用 [...所有出現之處...] 功能表選項來取代所找到的每個所選運算式，而不只是您已明確醒目標示的運算式。

## <a name="see-also"></a>另請參閱

[程式碼產生](../code-generation-in-visual-studio.md)  
[預覽變更](../../ide/preview-changes.md)
