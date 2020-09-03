---
title: 步驟 5：加入標籤參考 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671733"
---
# <a name="step-5-add-label-references"></a>步驟 5：加入標籤參考
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

程式需要追蹤玩家所選擇的 Label 控制項。 現在，程式會顯示玩家選擇的所有標籤。 但是，我們將要變更該行為。 在選擇第一個標籤之後，程式應該會顯示標籤的圖示。 在選擇第二個標籤之後，程式應該要短暫顯示這兩個圖示，然後再次隱藏這兩個圖示。 您的程式現在將會追蹤第一次選擇的 label 控制項，以及使用 *參考變數*選擇的第二個標籤控制項。

### <a name="to-add-label-references"></a>若要加入標籤參考

1. 使用下列程式碼，將標籤參考加入至您的表單。

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     這些參考變數看起來類似您先前用來將物件 (例如 `Timer` 物件、`List` 物件及 `Random` 物件) 加入至表單的陳述式。 但是，這些陳述式不會導致表單上出現兩個額外的 Label 控制項，因為這兩個陳述式中都沒有使用 `new` 關鍵字。 若沒有 `new` 關鍵字，就不會建立物件。 這就是為何 `firstClicked` 和 `secondClicked` 都稱為參考變數：它們只會追蹤 (或參照) `Label` 物件。

     當變數未追蹤物件時，該變數會設為特殊的保留值：在 Visual C# 中為 `null`，而在 Visual Basic 中為 `Nothing`。 因此當程式啟動時，`firstClicked` 和 `secondClicked` 會設為 `null` 或 `Nothing`，這表示變數並未追蹤任何項目。

2. 修改 Click 事件處理常式，以使用新的 `firstClicked` 參考變數。 移除 `label_Click()` 事件處理常式方法 (`clickedLabel.ForeColor = Color.Black;`) 中的最後一個陳述式，並以後面的 `if` 陳述式取代  (請務必包含註解和整個 `if` 陳述式)。

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. 儲存並執行您的程式。 選擇其中一個 Label 控制項，其圖示就會出現。

4. 選擇一個 Label 控制項，並注意什麼事也沒發生。 程式已經在追蹤玩家所選擇的第一個標籤，所以 `firstClicked` 不等於 Visual C# 中的 `null` 或 Visual Basic 中的 `Nothing`。 當 `if` 陳述式檢查 `firstClicked` 以判斷它是否等於 `null` 或 `Nothing` 時，若發現不相等，就不會執行 `if` 陳述式中的陳述式。 因此只有選擇的第一個圖示會變成黑色，而其他圖示則看不見，如下列圖片所示。

     ![顯示一個圖示的配對遊戲](../ide/media/express-tut4step5.png "Express_Tut4Step5") 顯示一個圖示的配對遊戲

     您可以在教學課程的下一個步驟中加入 **Timer** 控制項，以解決此問題。

### <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 [步驟6：加入計時器](../ide/step-6-add-a-timer.md)。

- 若要回到上一個教學課程步驟，請參閱 [步驟4：將 Click 事件處理常式加入至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)。
