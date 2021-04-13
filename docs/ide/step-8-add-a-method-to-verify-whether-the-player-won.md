---
title: 步驟 8：新增驗證玩家是否勝利的方法
description: 瞭解如何新增方法來判斷玩家是否贏了。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931e39a4f3cf87fe2d147d90f2111c9a9db3faeb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296998"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>步驟 8：新增驗證玩家是否勝利的方法
您已建立一個有趣的遊戲，但它需要額外的項目才能完成。 這個遊戲應該在玩家獲勝時結束，因此您需要加入 `CheckForWinner()` 方法以驗證玩家是否贏了。

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>若要加入方法來驗證玩家是否贏了

1. 將 `CheckForWinner()` 方法加入至您的程式碼下方 (位於 `timer1_Tick()` 事件處理常式下方)，如下列程式碼所示。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > 您可以使用此頁面右上方的程式設計語言控制項來查看 c # 程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)     

     方法會在中使用 `foreach` c # 或迴圈中的另一個迴圈 `For Each` ，Visual Basic 中的每個標籤都經過 <xref:System.Windows.Forms.TableLayoutPanel> 。 它會使用 c # 中的等號比較運算子 (`==` 和 `=` Visual Basic) 來檢查每個標籤的圖示色彩，以確認它是否符合背景。 如果色彩符合，則圖示會維持不可見狀態，而且玩家尚未配對剩餘的所有圖示。 在這種情況下，程式會使用 `return` 陳述式略過此方法的其餘部分。 如果迴圈通過所有的標籤，但未執行 `return` 陳述式，這表示已配對表單上的所有的圖示。 程式會顯示 MessageBox 恭喜玩家獲勝的播放程式，然後呼叫表單的 `Close()` 方法以結束遊戲。

2. 接下來，讓標籤的 <xref:System.Windows.Forms.Control.Click> 事件處理常式呼叫新的 `CheckForWinner()` 方法。 確定您的程式會在顯示玩家所選擇的第二個圖示之後立即檢查贏家。 尋找您在其中設定第二個已選擇圖示之色彩的程式碼行，然後立即呼叫 `CheckForWinner()` 方法，如下列程式碼所示。

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. 儲存並執行程式。 玩遊戲並將所有的圖示配對。 當您贏得時，程式會顯示「祝賀 **MessageBox** (如下列螢幕擷取畫面所示) ，然後關閉該方塊。

     ![配對遊戲和 MessageBox](../ide/media/express_tut4step8.png)<br/>
***配對遊戲** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 **[步驟9：嘗試其他功能](../ide/step-9-try-other-features.md)**。

- 若要回到上一個教學課程步驟，請參閱 [步驟7：讓配對保持可見](../ide/step-7-keep-pairs-visible.md)。
