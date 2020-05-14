---
title: 步驟 8：新增方法以驗證玩家是否贏了
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881fa0d90390a059bea28cb19584381f814396d3
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579758"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>步驟 8：新增方法以驗證玩家是否贏了
您已建立一個有趣的遊戲，但它需要額外的項目才能完成。 這個遊戲應該在玩家獲勝時結束，因此您需要加入 `CheckForWinner()` 方法以驗證玩家是否贏了。

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>若要加入方法來驗證玩家是否贏了

1. 將 `CheckForWinner()` 方法加入至您的程式碼下方 (位於 `timer1_Tick()` 事件處理常式下方)，如下列程式碼所示。

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > 使用此頁面右上角的程式設計語言控制項查看 C# 程式碼片段或 Visual Basic 程式碼片段。<br><br>![程式設計語言控制Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     該方法使用 C# 或 Visual `For Each` Basic 中的迴圈中的另一個<xref:System.Windows.Forms.TableLayoutPanel>`foreach`迴圈來遍歷 中的每個標籤。 它使用相等運算子（`==`在 C#`=`和 Visual Basic 中）檢查每個標籤的圖示顏色，以驗證它是否與背景匹配。 如果色彩符合，則圖示會維持不可見狀態，而且玩家尚未配對剩餘的所有圖示。 在這種情況下，程式會使用 `return` 陳述式略過此方法的其餘部分。 如果迴圈通過所有的標籤，但未執行 `return` 陳述式，這表示已配對表單上的所有的圖示。 程式會顯示 MessageBox 恭喜玩家獲勝的播放程式，然後呼叫表單的 `Close()` 方法以結束遊戲。

2. 接下來，讓標籤的 <xref:System.Windows.Forms.Control.Click> 事件處理常式呼叫新的 `CheckForWinner()` 方法。 確定您的程式會在顯示玩家所選擇的第二個圖示之後立即檢查贏家。 尋找您在其中設定第二個已選擇圖示之色彩的程式碼行，然後立即呼叫 `CheckForWinner()` 方法，如下列程式碼所示。

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. 儲存並執行程式。 玩遊戲並將所有的圖示配對。 獲勝後，程式將顯示一個祝賀**訊息方塊**（如以下螢幕截圖所示），然後關閉該框。

     ![配對遊戲和 MessageBox](../ide/media/express_tut4step8.png)<br/>
***匹配遊戲****與****訊息方塊***

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 要轉到下一個教程步驟，請參閱**[步驟 9：嘗試其他功能](../ide/step-9-try-other-features.md)**。

- 要返回到前面的教程步驟，請參閱步驟[7：保持對可見](../ide/step-7-keep-pairs-visible.md)。
