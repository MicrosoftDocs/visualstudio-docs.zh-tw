---
title: 步驟 6：新增計時器
description: 瞭解如何將控制項新增 <xref:System.Windows.Forms.Timer> 至配對遊戲。
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2684b197fc32b33081c8ecdfa8139b3c8f14e752
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480547"
---
# <a name="step-6-add-a-timer"></a>步驟 6：新增計時器
接下來，您可以將 <xref:System.Windows.Forms.Timer> 控制項新增至配對遊戲。 計時器會等候指定的毫秒數，然後引發事件，稱為「刻度」。 這對於定期啟動動作或重複動作非常有用。 在這個案例中，您將使用計時器讓玩家選擇兩個圖示，如果圖示不相符，則在短時間之後再次隱藏兩個圖示。

## <a name="to-add-a-timer"></a>若要加入計時器

1. 在 [Windows Forms 設計工具] 的工具箱中，選擇 [計時器] (位於 [元件] 類別)，然後選擇 **Enter** 鍵，按兩下計時器，將計時器控制項新增至表單。 計時器的圖示（稱為 **Timer1**）應該會出現在表單下方的空間中，如下圖所示。

     ![計時器](../ide/media/express_timer.png)<br/>
**_計時器_* _

    > [!NOTE]
    > 如果工具箱是空的，請確定先選取表單設計工具 (而不是選取表單的後置程式碼)，再開啟工具箱。

2. 選擇 _ *Timer1** 圖示來選取計時器。 在 [屬性] 視窗中，從檢視事件切換為檢視屬性。 然後，將計時器的 [Interval] 屬性設為 [750]，但是將 [Enabled] 屬性設為 [False]。 **Interval** 屬性會告知計時器在「刻度」之間，或當其觸發其 <xref:System.Windows.Forms.Timer.Tick> 事件時應等候多久的時間。 值為 750 表示會告知計時器等待四分之三秒 (750 毫秒)，再引發其 Tick 事件。 您只會在玩家選擇第二個標籤時呼叫 <xref:System.Windows.Forms.Timer.Start> 方法，以啟動計時器。

3. 選擇 [Windows Forms 設計工具] 中的計時器控制項圖示，然後選擇 **Enter** 鍵或按兩下計時器，以新增空的 Tick 事件處理常式。 以下列程式碼取代程式碼，或手動輸入下列程式碼至事件處理常式。

     [!code-csharp[VbExpressTutorial4Step6#7](../ide/codesnippet/CSharp/step-6-add-a-timer_1.cs)]
     [!code-vb[VbExpressTutorial4Step6#7](../ide/codesnippet/VisualBasic/step-6-add-a-timer_1.vb)]

      > [!IMPORTANT]
      > 您可以使用此頁面右上方的程式設計語言控制項來查看 c # 程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

     Tick 事件處理常式會執行下列三件事情：首先，它會呼叫 <xref:System.Windows.Forms.Timer.Stop> 方法來確定計時器並未執行。 接著，它會使用兩個參考變數 `firstClicked` 和 `secondClicked`，確定玩家所選的兩個標籤的圖示再次看不見。 最後，它會將 `firstClicked` 和 `secondClicked` 參考變數重設為 `null` c # 和 Visual Basic 中的 `Nothing` 。 這個步驟很重要，因為這就是程式本身重設的方式。 現在它不會追蹤任何的 <xref:System.Windows.Forms.Label> 控制項，而且已準備好讓玩家再度選擇標籤。

    > [!NOTE]
    > Timer 物件具有一個 `Start()` 方法可以啟動計時器，還有一個 `Stop()` 方法可以停止計時器。 當您在 [屬性] 視窗中將計時器的 [Enabled] 屬性設為 [True] 時，計時器會在程式開始時立即開始計時。 但是，當您將它設為 [False] 時，則要等到呼叫其 `Start()` 方法時才會開始計時。 通常，計時器會不斷地引發其 Tick 事件，並使用 [Interval] 屬性來決定在刻度之間要等待多少毫秒。 您可能已注意到在 Tick 事件內呼叫計時器之 `Stop()` 方法的方式。 該方式會使計時器進入「一次性模式」，表示在呼叫 `Start()` 方法時，它會等候指定的間隔、觸發單一 Tick 事件，然後停止。

4. 若要查看作用中的新計時器，請移至程式碼編輯器並將下列程式碼加入至 `label_Click()` 事件處理常式方法的頂端和底端   (您要將兩個 `if` 語句加入至頂端，並將三個語句新增至底部，則方法的其餘部分會維持不變。 ) 

     [!code-csharp[VbExpressTutorial4Step6#8](../ide/codesnippet/CSharp/step-6-add-a-timer_2.cs)]
     [!code-vb[VbExpressTutorial4Step6#8](../ide/codesnippet/VisualBasic/step-6-add-a-timer_2.vb)]

     位於方法頂端的程式碼會檢查計時器是否藉由核取 [Enabled] 屬性的值來啟動。 如此一來，如果玩家選擇第一個和第二個 Label 控制項而且計時器啟動了，則選擇第三個標籤後並不會執行任何動作。 它也可防止播放程式在遊戲準備好進行另一個點擊之前，快速按一下第三次。 

     位於方法底端的程式碼會設定 `secondClicked` 參考變數，以便追蹤玩家所選擇的第二個 Label 控制項，然後再將該標籤的圖示色彩設成黑色，使其能被看見。 然後，它會以一次性模式啟動計時器，因此會等待 750 毫秒，而後引發單一 Tick 事件。 計時器的 Tick 事件處理常式會隱藏兩個圖示，並重設 `firstClicked` 和 `secondClicked` 參考變數，以便表單準備讓玩家選擇另一組圖示。

5. 儲存並執行您的程式。 選擇圖示，它會成為可見狀態。

6. 請選擇其他圖示。 它會短暫出現，然後這兩個圖示會消失。 重複此動作許多次。 表單現在會追蹤您選擇的第一個和第二個圖示，並使用計時器在圖示消失之前暫停追蹤。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 **[步驟7：讓配對保持可見](../ide/step-7-keep-pairs-visible.md)**。

- 若要返回上一個教學課程步驟，請參閱[步驟 5：新增標籤參考](../ide/step-5-add-label-references.md)。
