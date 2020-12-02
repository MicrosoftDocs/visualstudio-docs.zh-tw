---
title: 教學課程 2：建立計時的數學測驗
description: 瞭解如何建立測驗，讓測驗者必須在指定的時間內回答四個隨機的算術問題。
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b0044e5d3a08e46318a325443e9f05742e141127
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479104"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>教學課程 2：建立計時的數學測驗

在本教學課程中，您將會建置一項測驗，在測驗中，受測者必須在指定的時間內回答四個隨機的算術問題。

> [!NOTE]
> 本教學課程涵蓋 c # 和 Visual Basic，因此著重于您所使用之程式設計語言的特定資訊。

本教學課程會逐步引導您完成下列工作：

- 使用 <xref:System.Random> 類別產生隨機數字。

- 使用 <xref:System.Windows.Forms.Timer> 控制項觸發事件，使其在特定時間發生。

- 使用 `if else` 陳述式控制程式流程。

- 在程式碼中執行基本的算術運算。

當您完成時，您的測驗看起來會像下列螢幕擷取畫面，但不同的數位除外：

![包含四個問題的數學測驗](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>教學課程的連結

|標題|描述|
|-----------|-----------------|
|[步驟 1：建立專案並將標籤新增至表單](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|從建立專案、變更屬性，然後新增 `Label` 控制項開始。|
|[步驟 2：建立隨機加法問題](../ide/step-2-create-a-random-addition-problem.md)|建立加法問題，並使用 `Random` 類別產生隨機數字。|
|[步驟 3：新增倒數計時器](../ide/step-3-add-a-countdown-timer.md)|加入倒數計時器，以便在測驗時進行計時。|
|[步驟 4：新增 CheckTheAnswer() 方法](../ide/step-4-add-the-checktheanswer-parens-method.md)|加入方法檢查受測者是否輸入問題的正確答案。|
|[步驟 5：新增 NumericUpDown 控制項的 Enter 事件處理常式](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|加入事件處理常式，讓您的測驗更容易進行。|
|[步驟 6：新增減法問題](../ide/step-6-add-a-subtraction-problem.md)|加入產生隨機數字、使用計時器並且會檢查答案是否正確的減法問題。|
|[步驟 7：新增乘法及除法問題](../ide/step-7-add-multiplication-and-division-problems.md)|加入產生隨機數字、使用計時器並且會檢查答案是否正確的乘法和除法問題。|
|[步驟 8：自訂測驗](../ide/step-8-customize-the-quiz.md)|嘗試其他功能，例如變更色彩和加入提示。|

另外還有絕佳的免費影片學習資源可供您使用。 若要深入瞭解如何在 c # 中進行程式設計，請參閱 [c # 基礎：適用于絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

若要開始本教學課程，請從 **[步驟1：建立專案並將標籤新增至您的表單](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**。

## <a name="see-also"></a>另請參閱

* [其他 c # 教學課程](../get-started/csharp/index.yml)
* [Visual Basic 教學課程](../get-started/visual-basic/index.yml)
* [C + + 教學課程](/cpp/get-started/tutorial-console-cpp)