---
title: 教學課程 2：建立計時的數學測驗
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b1f3620ef462228ff6a3461f44019e9c515a1c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579311"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>教學課程 2：建立計時的數學測驗

在本教學課程中，您將會建置一項測驗，在測驗中，受測者必須在指定的時間內回答四個隨機的算術問題。

> [!NOTE]
> 本教程將介紹 C# 和 Visual Basic，因此請關注特定于您使用的程式設計語言的資訊。

本教程將引導您完成以下任務：

- 使用 <xref:System.Random> 類別產生隨機數字。

- 使用 <xref:System.Windows.Forms.Timer> 控制項觸發事件，使其在特定時間發生。

- 使用 `if else` 陳述式控制程式流程。

- 在程式碼中執行基本的算術運算。

完成後，您的測驗將類似于以下螢幕截圖，除非具有不同的數位：

![包含四個問題的數學測驗](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>教學課程的連結

|Title|描述|
|-----------|-----------------|
|[第 1 步：創建專案並將標籤添加到表單](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|從建立專案、變更屬性，然後新增 `Label` 控制項開始。|
|[步驟 2：建立隨機加法問題](../ide/step-2-create-a-random-addition-problem.md)|建立加法問題，並使用 `Random` 類別產生隨機數字。|
|[步驟 3：加入倒數計時器](../ide/step-3-add-a-countdown-timer.md)|加入倒數計時器，以便在測驗時進行計時。|
|[步驟 4：加入 CheckTheAnswer() 方法](../ide/step-4-add-the-checktheanswer-parens-method.md)|加入方法檢查受測者是否輸入問題的正確答案。|
|[步驟 5：加入 NumericUpDown 控制項的事件處理常式](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|加入事件處理常式，讓您的測驗更容易進行。|
|[步驟 6：加入減法問題](../ide/step-6-add-a-subtraction-problem.md)|加入產生隨機數字、使用計時器並且會檢查答案是否正確的減法問題。|
|[步驟 7：加入乘法和除法問題](../ide/step-7-add-multiplication-and-division-problems.md)|加入產生隨機數字、使用計時器並且會檢查答案是否正確的乘法和除法問題。|
|[第 8 步：自訂測驗](../ide/step-8-customize-the-quiz.md)|嘗試其他功能，例如變更色彩和加入提示。|

也有偉大的，免費的視頻學習資源可供你使用。 要瞭解有關 C# 中程式設計的更多詳細資訊，請參閱[C# 基礎知識：絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

要開始本教程，請從步驟 1 開始**[：創建專案並將標籤添加到表單](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** 中。

## <a name="see-also"></a>另請參閱

* [更多 C# 教程](/visualstudio/get-started/csharp/)
* [Visual Basic 教學課程](/visualstudio/get-started/visual-basic/)
* [C++教程](/cpp/get-started/tutorial-console-cpp)
