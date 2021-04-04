---
title: 步驟 5：新增標籤參考
description: 瞭解如何將標籤參考新增至您的表單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 316db91ac00ca9e18b9c0875340d2358b8955bed
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214222"
---
# <a name="step-5-add-label-references"></a>步驟 5：新增標籤參考
程式需要追蹤玩家所選擇的 Label 控制項。 現在，程式會顯示玩家選擇的所有標籤。 但是，我們將要變更該行為。 在選擇第一個標籤之後，程式應該會顯示標籤的圖示。 在選擇第二個標籤之後，程式應該要短暫顯示這兩個圖示，然後再次隱藏這兩個圖示。 您的程式現在將會使用 *參考變數*，追蹤第一次和第二次選擇的 Label 控制項。

## <a name="to-add-label-references"></a>若要加入標籤參考

1. 使用下列程式碼，將標籤參考加入至您的表單。

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > 您可以使用此頁面右上方的程式設計語言控制項來查看 c # 程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

     這些參考變數看起來類似您先前用來將物件 (例如 <xref:System.Windows.Forms.Timer> 物件、<xref:System.Collections.Generic.List%601> 物件及 <xref:System.Random> 物件) 加入至表單的陳述式。 但是，這些陳述式不會導致表單上出現兩個額外的 Label 控制項，因為這兩個陳述式中都沒有使用 `new` 關鍵字。 若沒有 `new` 關鍵字，就不會建立物件。 這就是為何 `firstClicked` 和 `secondClicked` 都稱為參考變數：它們只會追蹤 (或參照) Label 物件。

     當變數未追蹤物件時，它會設定為特殊的保留值： `null` 在 c # 中和 `Nothing` Visual Basic 中。 因此當程式啟動時，`firstClicked` 和 `secondClicked` 會設為 `null` 或 `Nothing`，這表示變數並未追蹤任何項目。

2. 修改 <xref:System.Windows.Forms.Control.Click> 事件處理常式，以使用新的 `firstClicked` 參考變數。 移除 `label_Click()` 事件處理常式方法 (`clickedLabel.ForeColor = Color.Black;`) 中的最後一個陳述式，並以後面的 `if` 陳述式取代  (請務必包含註解和整個 `if` 陳述式)。

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. 儲存並執行您的程式。 選擇其中一個 Label 控制項，其圖示就會出現。

4. 選擇一個 Label 控制項，並注意什麼事也沒發生。 程式已經在追蹤玩家所選擇的第一個標籤，因此 `firstClicked` 不等於 `null` c # 或 `Nothing` Visual Basic 中的。 當 `if` 陳述式檢查 `firstClicked` 以判斷它是否等於 `null` 或 `Nothing` 時，若發現不相等，就不會執行 `if` 陳述式中的陳述式。 因此，只有所選的第一個圖示會變成黑色，而其他圖示則看不見，如下列影像所示。

     ![顯示一個圖示的配對遊戲](../ide/media/express_tut4step5.png)<br/>
***配對遊戲** _ _showing 一個圖示 *

     您可以在教學課程的下一個步驟中加入 **Timer** 控制項，以解決此問題。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 **[步驟6：加入計時器](../ide/step-6-add-a-timer.md)**。

- 若要返回前一個教學課程步驟，請參閱[步驟 4：將 Click 事件處理常式加入至每個標籤](../ide/step-4-add-a-click-event-handler-to-each-label.md)。
