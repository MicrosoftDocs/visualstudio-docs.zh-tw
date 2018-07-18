---
title: 步驟 5：加入標籤參考
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8ecea1c6a1baf27247b9b01d28e04b6da827a0e3
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747941"
---
# <a name="step-5-add-label-references"></a>步驟 5：加入標籤參考
程式需要追蹤玩家所選擇的 Label 控制項。 現在，程式會顯示玩家選擇的所有標籤。 但是，我們將要變更該行為。 在選擇第一個標籤之後，程式應該會顯示標籤的圖示。 在選擇第二個標籤之後，程式應該要短暫顯示這兩個圖示，然後再次隱藏這兩個圖示。 您的程式現在將會使用*參考變數*，追蹤第一次和第二次選擇的 Label 控制項。

## <a name="to-add-label-references"></a>若要加入標籤參考

1.  使用下列程式碼，將標籤參考加入至您的表單。

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     這些參考變數看起來類似您先前用來將物件 (例如 <xref:System.Windows.Forms.Timer> 物件、<xref:System.Collections.Generic.List%601> 物件及 <xref:System.Random> 物件) 加入至表單的陳述式。 但是，這些陳述式不會導致表單上出現兩個額外的 Label 控制項，因為這兩個陳述式中都沒有使用 `new` 關鍵字。 若沒有 `new` 關鍵字，就不會建立物件。 這就是為何 `firstClicked` 和 `secondClicked` 都稱為參考變數：它們只會追蹤 (或參照) Label 物件。

     當變數未追蹤物件時，該變數會設為特殊的保留值：在 Visual C# 中為 `null`，而在 Visual Basic 中為 `Nothing`。 因此當程式啟動時，`firstClicked` 和 `secondClicked` 會設為 `null` 或 `Nothing`，這表示變數並未追蹤任何項目。

2.  修改 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以使用新的 `firstClicked` 參考變數。 移除 `label_Click()` 事件處理常式方法 (`clickedLabel.ForeColor = Color.Black;`) 中的最後一個陳述式，並以後面的 `if` 陳述式取代  (請務必包含註解和整個 `if` 陳述式)。

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3.  儲存並執行您的程式。 選擇其中一個 Label 控制項，其圖示就會出現。

4.  選擇一個 Label 控制項，並注意什麼事也沒發生。 程式已經在追蹤玩家所選擇的第一個標籤，所以 `firstClicked` 不等於 Visual C# 中的 `null` 或 Visual Basic 中的 `Nothing`。 當 `if` 陳述式檢查 `firstClicked` 以判斷它是否等於 `null` 或 `Nothing` 時，若發現不相等，就不會執行 `if` 陳述式中的陳述式。 因此只有選擇的第一個圖示會變成黑色，而其他圖示則看不見，如下列圖片所示。

     ![顯示一個圖示的配對遊戲](../ide/media/express_tut4step5.png)
顯示一個圖示的**配對遊戲**

     您可以在教學課程的下一個步驟中加入 **Timer** 控制項，以解決此問題。

## <a name="to-continue-or-review"></a>若要繼續或檢視

-   若要移到下一個教學課程步驟，請參閱[步驟 6：加入計時器](../ide/step-6-add-a-timer.md)。

-   若要返回前一個教學課程步驟，請參閱[步驟 4：將 Click 事件處理常式加入至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)。
