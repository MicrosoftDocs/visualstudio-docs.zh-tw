---
title: 步驟 10：為其他按鈕及核取方塊撰寫程式碼
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281c98ca52b6dd18ee726e3191d47d6755fd8326
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293611"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>步驟 10：為其他按鈕及核取方塊撰寫程式碼

現在，您可以準備完成其他四個方法。 您可以複製及貼上此程式碼，但如果想要充分學習本教學課程，請輸入程式碼並使用 IntelliSense。

這個程式碼會在您之前加入的按鈕上加入功能。 若沒有這個程式碼，按鈕就不會有任何作用。 按鈕會在其 <xref:System.Windows.Forms.Control.Click> 事件中使用程式碼 (而核取方塊會使用 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件)，在您啟動控制項時執行不同的動作。 例如， `clearButton_Click` `ClearButton_Click`（或）事件會在您選擇 [**清除圖片**] 按鈕時啟動，藉由將目前影像的**image**屬性設為**null** （或不提供**任何**專案）來清除。 程式碼中的每個事件都包括註解，用於說明程式碼的功能。

> [!TIP]
> 最佳做法：一律為程式碼加上註解。 註解是供使用者閱讀的資訊，值得花時間讓您的程式碼變得更易於理解。 程式會忽略註解行上的任何文字。 在C#中，您會在開頭（//）輸入兩個正斜線來批註一行，而在 Visual Basic 您會以單引號（'）開頭來批註一行。

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>如何撰寫其他按鈕和核取方塊的程式碼

將下列程式碼加入至 **Form1** 程式碼檔 (*Form1.cs* 或 *Form1.vb*)。
> [!IMPORTANT]
> 使用此頁面右上方的程式設計語言控制項，以查看C#程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

## <a name="next-steps"></a>後續步驟

* 若要前往下一個教學課程步驟，請參閱[步驟 11：執行您的程式並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)。

* 若要回到上一個教學課程步驟，請參閱[步驟 9：檢閱、註解和測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)。

## <a name="see-also"></a>另請參閱

* [教學課程 2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程 3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
