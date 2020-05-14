---
title: 步驟 10：撰寫其他按鈕和核取方塊的程式碼
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579433"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>步驟 10：撰寫其他按鈕和核取方塊的程式碼

現在，您可以準備完成其他四個方法。 您可以複製及貼上此程式碼，但如果想要充分學習本教學課程，請輸入程式碼並使用 IntelliSense。

這個程式碼會在您之前加入的按鈕上加入功能。 若沒有這個程式碼，按鈕就不會有任何作用。 按鈕會在其 <xref:System.Windows.Forms.Control.Click> 事件中使用程式碼 (而核取方塊會使用 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件)，在您啟動控制項時執行不同的動作。 `clearButton_Click`例如，`ClearButton_Click`在選擇 **"清除圖片"** 按鈕時啟動的 （或 ） 事件會通過其**Image**屬性設置為**null（** 或**無任何**）來擦除當前圖像。 程式碼中的每個事件都包括註解，用於說明程式碼的功能。

> [!TIP]
> 最好的做法是永遠為程式碼加上註解。 註解是供使用者閱讀的資訊，值得花時間讓您的程式碼變得更易於理解。 應用將忽略注釋行上的所有內容。 在 C# 中，通過在開頭 （//） 鍵入兩個正向斜杠來注釋行，在 Visual Basic 中，您從單個引號 （'） 開始注釋行。

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>如何為其他按鈕和核取方塊編寫代碼

將下列程式碼加入至 **Form1** 程式碼檔 (*Form1.cs* 或 *Form1.vb*)。

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> 您的代碼可能不會顯示"camelCase"字母。

## <a name="next-steps"></a>後續步驟

* 要轉到下一個教程步驟，請參閱**[步驟 11：運行你的應用並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)**。

* 若要回到上一個教學課程步驟，請參閱[步驟 9：檢閱、註解和測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
