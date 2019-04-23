---
title: 步驟 3：加入倒數計時器 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f0b98fa4b3182db71567d61569cddf4cfae33ec1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094812"
---
# <a name="step-3-add-a-countdown-timer"></a>步驟 3：新增倒數計時器
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本教學課程的第三個部分中，您將加入倒數計時器來追蹤受測者可完成作答的剩餘秒數。  
  
> [!NOTE]
>  這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。  
  
### <a name="to-add-a-countdown-timer"></a>若要加入倒數計時器  
  
1. 加入名為 **timeLeft** 的整數變數，就像在前一個程序中所進行。 您的程式碼應該看起來與下列範例相同。  
  
     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]  
  
     現在您需要實際計算秒數的方法，例如計時器，它會在經過您指定的時間後引發事件。  
  
2. 在設計視窗中，將 `Timer` 控制項從 [工具箱] 的 [元件] 分類移至表單。  
  
     控制項會出現在設計視窗底部的灰色區域中。  
  
3. 在表單上選擇您剛新增的 [timer1] 圖示，並將其 [Interval] 屬性設定為 [1000]。  
  
     由於間隔值為毫秒，因此 1000 這個值會讓 Tick 事件每秒引發一次。  
  
4. 在表單上按兩下 [Timer] 控制項，或選擇該控制項，然後選擇 Enter 鍵。  
  
     程式碼編輯器隨即出現，並且顯示您剛才為 Tick 事件處理常式加入的方法。  
  
5. 將下列陳述式加入至新的事件處理常式方法。  
  
     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]  
  
     根據您新增的項目，計時器會藉由判斷 **timeLeft** 整數變數是否大於 0，每秒檢查一次時間是否已結束。 如果是，表示仍有剩餘時間。 計時器會先將 timeLeft 減 1，然後更新 `timeLabel` 控制項的 [Text] 屬性，讓受測者看到還剩多少秒。  
  
     如果沒有剩餘時間，計時器就會停止，並將 `timeLabel` 控制項的文字變更為顯示 **Time's up!**。 此時會出現訊息方塊宣布測驗結束，並且公布答案，這個案例為 addend1 和 addend2 相加。 `startButton` 控制項的 [Enabled] 屬性會設定為 `true`，如此受測者就能開始另一項測驗。  
  
     您已加入 `if else` 陳述式，讓程式知道如何做判斷。 `if else` 陳述式看起來如下。  
  
    > [!NOTE]
    >  下列範例僅供參考，請不要將它加入您的專案中。  
  
    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  
  
    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  
  
     仔細查看您在 `else` 區塊中加入，用來顯示加法問題答案的陳述式。  
  
     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]  
  
     `addend1 + addend2` 陳述式會將兩個變數中的值相加。 第一個部分 (`sum.Value`) 會使用 sum (總和) `NumericUpDown` 控制項的 [Value] 屬性來顯示正確答案。 稍後您會使用相同屬性檢查測驗的答案。  
  
     受測者透過使用 `NumericUpDown` 控制項就能更輕鬆地輸入數字，這就是為何使用其中一個控制項輸入數學問題答案的原因。 所有可能的答案包括從 0 到 100 的整數。 藉由保留 [Minimum]、[Maximum] 和 [DecimalPlaces] 屬性的預設值，就能確保受測者無法輸入小數、負數或太大的數字 (如果您要允許受測者輸入 3.141 而不是 3.1415，可以將 [DecimalPlaces] 屬性設定為 3)。  
  
6. 將三行程式碼加入至 `StartTheQuiz()` 方法的結尾，使程式碼看起來如下。  
  
     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]  
  
     現在，當測驗開始時，[timeLeft] 變數會設定為 30，而且 `timeLabel` 控制項的 [Text] 屬性會設定為 30 秒。 然後，`Timer` 控制項的 `Start()` 方法就會開始倒數計時 (測驗還不會檢查答案，這是下一個部分)。  
  
7. 儲存您的程式，並執行程式，然後選擇表單上的 [開始] 按鈕。  
  
     計時器就會開始倒數。 當時間結束時，測驗就會結束，答案也會出現。 下圖將顯示進行中的測驗。  
  
     ![數學測驗正在進行中](../ide/media/express-addcountdown.png "Express_AddCountdown")  
數學測驗正進行中  
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
- 若要前往下一個教學課程步驟，請參閱[步驟 4：新增 checktheanswer （） 方法](../ide/step-4-add-the-checktheanswer-parens-method.md)。  
  
- 若要回到上一個教學課程步驟，請參閱[步驟 2：建立隨機加法問題](../ide/step-2-create-a-random-addition-problem.md)。
