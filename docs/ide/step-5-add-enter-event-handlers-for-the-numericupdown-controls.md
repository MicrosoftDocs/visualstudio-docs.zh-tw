---
title: 針對 NumericUpDown 控制項新增 Enter 事件處理常式
description: 在「建立計時的數學測驗」教學課程中，新增 NumericUpDown 控制項的 Enter 事件處理常式。
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef6207ebfa30401896a7681b599128cfb9648e96
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296322"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>步驟 5：新增 NumericUpDown 控制項的 Enter 事件處理常式

在本教學課程的第五個部分中，您將加入 <xref:System.Windows.Forms.Control.Enter> 事件處理常式，讓輸入測驗問題的答案時更加容易。 只要受測者選擇並開始輸入不同的值，這個程式碼就會選取並清除每個 <xref:System.Windows.Forms.NumericUpDown> 控制項中的目前值。

> [!NOTE]
> 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

## <a name="to-verify-the-default-behavior"></a>若要驗證預設行為

1. 執行程式並開始進行測驗。

     在加法問題的 **NumericUpDown** 控制項中，游標會在 **0** (零) 旁邊閃爍。

2. 輸入 **3**，並注意控制項會顯示 **30**。

3. 輸入 **5** 並注意會出現 **350**，但是會在一秒後變成 **100**。

     在解決此問題之前，請先思考到底發生什麼事。 請思考，當您輸入 **3** 時，為什麼 **0** 沒有消失，以及為什麼 **350** 變成 **100**，但不是立即變更。

     這個行為似乎有些奇怪，不過對於程式碼邏輯而言是合理的。 當您選擇 [開始] 按鈕時，它的 [Enabled] 屬性會設定為 [False]，所以按鈕會呈現灰色且無法使用。 您的程式會將目前的選取項目 (焦點) 切換到具有次低 TabIndex 值的控制項，也就是加法問題的 NumericUpDown 控制項。 當您使用 **Tab** 鍵移至 NumericUpDown 控制項時，游標會自動定位在控制項開頭，這就是為什麼您輸入的數字會從左邊出現，而不是從右邊出現的原因。 如果您指定的值大於 [MaximumValue] 屬性的值 (該值設為 100)，該屬性的值就會取代您輸入的數字。

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>若要加入 NumericUpDown 控制項的 Enter 事件處理常式

1. 選擇表單上的第一個 **NumericUpDown** 控制項 (名為 "sum")，然後在 [屬性] 對話方塊中選擇工具列上的 [事件] 圖示。

   ![屬性工具列中的事件按鈕](media/control-properties-events.png)

   [屬性] 對話方塊中的 [事件] 索引標籤會顯示可以針對表單上所選擇項目回應 (處理) 的所有事件。 由於您選擇了 NumericUpDown 控制項，因此所有列出的事件都會與該控制項相關。

2. 選擇 **Enter** 事件、輸入 `answer_Enter`，然後按 **Enter** 鍵。

   ![Enter 事件處理常式方法名稱](media/enter-event.png)

   現在您已為 sum NumericUpDown 控制項加入 Enter 事件處理常式，並且將處理常式命名為 **answer_Enter**。

3. 在 **answer_Enter** 事件處理常式的方法中，新增下列程式碼：

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs" id="Snippet11":::

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     這個程式碼看似複雜，但是逐步查看後就能了解它。 首先，查看方法的頂端：C# 中的 `object sender` 或 Visual Basic 中的 `sender As System.Object`。 這個參數會參考要引發其事件的物件，稱為 sender。 在這個案例中，sender 物件為 NumericUpDown 控制項。 因此，在方法的第一行中，您會指定 sender 不是一般物件，而是更具體的 NumericUpDown 控制項   (每個 NumericUpDown 控制項都是一個物件，但並非每個物件都是 NumericUpDown 控制項。在此方法中，) NumericUpDown 控制項的名稱為 **answerBox** ，因為它將用於表單上的所有 NumericUpDown 控制項，而不只是 sum NumericUpDown 控制項。 由於您是在這個方法中宣告 answerBox 變數，因此其範圍僅適用於這個方法。 換句話說，變數只能夠在這個方法內使用。

     下一行驗證 answerBox 是否已成功從物件轉換 (轉型) 為 NumericUpDown 控制項。 如果轉換失敗，變數的值會是 `null` (C#) 或 `Nothing` (Visual Basic)。 第三行會取得 NumericUpDown 控制項中所出現答案的長度，而第四行會根據這個長度選取控制項中的目前值。 現在，當受測者選擇控制項時，Visual Studio 就會引發這個事件，進而選取目前的答案。 一旦受測者開始輸入不同的答案，就會立即清除上一個答案，並以新的答案取代。

4. 在 **Windows Forms 設計工具** 中，選擇 difference **NumericUpDown** 控制項。

5. 在 [屬性] 對話方塊的 [事件] 頁面中，向下捲動至 [Enter] 事件，並選擇該列結尾的下拉箭號，然後選擇您剛才新增的 `answer_Enter` 事件處理常式。

6. 針對 product (積數) 和 quotient (商數) NumericUpDown 控制項重複上述步驟。

7. 儲存程式並執行。

     當您選擇 **NumericUpDown** 控制項時，現有的值就會自動選取，然後在您開始輸入不同的值時清除。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 **[步驟6：新增減法問題](../ide/step-6-add-a-subtraction-problem.md)**。

- 若要回到上一個教學課程步驟，請參閱[步驟 4︰新增 CheckTheAnswer() 方法](../ide/step-4-add-the-checktheanswer-parens-method.md)。
