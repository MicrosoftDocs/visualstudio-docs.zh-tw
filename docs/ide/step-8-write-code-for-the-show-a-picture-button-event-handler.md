---
title: 為顯示圖片按鈕事件處理常式撰寫程式碼
description: 在 [建立圖片檢視器] 教學課程中，為 [顯示圖片] 按鈕事件處理常式撰寫程式碼。
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5529df07cc086ed80fad291b268e6a1a28f1d06a
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295412"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼

在此步驟中，您會將 [ **顯示圖片** ] 按鈕的運作方式如下：

- 當使用者選擇該按鈕時，應用程式會開啟一個 <xref:System.Windows.Forms.OpenFileDialog> box。

- 如果使用者開啟圖片檔案，則應用程式會在中顯示該圖片 <xref:System.Windows.Forms.PictureBox> 。

IDE 提供一個功能強大的工具，稱為 IntelliSense，可幫助您撰寫程式碼。 當您輸入程式碼時，IDE 會開啟一個方塊，其中包含您所輸入之部分文字的建議完成項。

IntelliSense 會嘗試判斷您接下來要做什麼，並自動跳至您從清單中選擇的最後一個專案。 您可以利用向上或向下箭號在清單中移動，也可以繼續輸入字母來縮小選項範圍。 當您看到想要的選項時，選擇 **Tab** 鍵加以選取。 或者，如果不需要的話，您也可以忽略建議。

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>為顯示圖片按鈕事件處理常式撰寫程式碼

1. 移至 **Windows Forms 設計工具**，然後按兩下 [顯示圖片] 按鈕。 IDE 會立即移至程式碼設計工具，然後將游標移到 `showButton_Click()` `ShowButton_Click()` 您先前新增的 (或) 方法內。

1. 在兩個大括弧 `{ }` 之間的空白行上鍵入 `i`  (在 Visual Basic 中，請在和之間的空白行上輸入 `Private Sub...` `End Sub` 。 ) **IntelliSense** 視窗隨即開啟，如下圖所示。

    ![包含 Visual C&#35; 程式碼的 IntelliSense](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > 您的程式碼可能無法顯示 "camelCase" 字母的事件處理常式。

1. [ **IntelliSense** ] 視窗應該會反白顯示該字 `if` 。  (如果沒有，請輸入小寫 `f` ，它就會。 ) 注意 [ **IntelliSense** ] 視窗旁的 *工具提示* 方塊如何出現，以及描述的 **程式碼片段（if 語句**）。  (在 Visual Basic 中，工具提示也會指出這是程式碼片段，但有稍微不同的用語。 ) 您想要使用該程式碼片段，請選擇 **Tab** 鍵以插入 `if` 程式碼中。 然後再次選擇 **Tab** 鍵來使用 `if` 程式碼片段。 (如果您選擇其他位置並造成 [IntelliSense] 視窗消失，請按退格鍵刪除 `i` 並重新鍵入，[IntelliSense] 視窗就會再次開啟)。

    ![Visual C&#35; 程式碼](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>使用 IntelliSense 來輸入更多程式碼

接下來，您使用 IntelliSense 輸入更多程式碼，以開啟 [開啟檔案] 對話方塊。 如果使用者選擇 [確定] 按鈕，則 PictureBox 會載入使用者選取的檔案。 下列步驟顯示如何進入程式碼，雖然有許多步驟，但這只是幾個按鍵：

 1. 從程式碼片段中選取的文字 **true** 開始。 鍵入 `op` 覆寫它 (在 Visual Basic 中，開頭是大寫，因此請鍵入 `Op`)。

 1. [IntelliSense] 視窗隨即開啟並顯示 [openFileDialog1]。 選擇 **Tab** 鍵加以選取。 (在 Visual Basic 中，它的開頭是大寫，因此您會看到 [OpenFileDialog1]。 確定已選取 [OpenFileDialog1])。

     若要深入了解 `OpenFileDialog`，請參閱 [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>)。

 1. 輸入一段期間 (`.`)  (許多程式設計人員都會呼叫這個點。 ) 因為您在 **openFileDialog1** 之後輸入了一個點， **IntelliSense** 視窗會隨即開啟，並填入 **OpenFileDialog** 元件的所有屬性和方法。 當您在 **Windows Forms 設計工具** 中選擇該元件時，[屬性] 視窗中也會顯示相同的屬性。 您也可以選擇指示元件執行動作 (例如開啟對話方塊) 的方法。

    > [!NOTE]
    > [IntelliSense] 視窗可以同時顯示屬性和方法。 若要判斷顯示的內容，請查看 [IntelliSense] 視窗中每個項目左方的圖示。 您會看到每個方法旁的區塊影像，以及每個屬性旁邊的扳手 (或 spanner) 的影像。 每一個事件旁邊也會出現閃電圖示。 <br><br>以下是顯示的圖示：<br><br>![方法圖示](../ide/media/express_iconmethod.png)<br>![屬性圖示](../ide/media/express_iconproperty.png)<br>![事件圖示](../ide/media/express_iconevent.png)

 1. 開始鍵入 `ShowDialog` (大小寫對 IntelliSense 而言不重要)。 `ShowDialog()` 方法會顯示 [開啟檔案] 對話方塊。 視窗反白顯示 **ShowDialog** 後，請選擇 **Tab** 鍵。 您也可以反白顯示 "ShowDialog" 並選擇 **F1** 鍵以取得其說明。

    若要深入了解 `ShowDialog()` 方法，請參閱 [ShowDialog 方法](<xref:System.Windows.Forms.Form.ShowDialog%2A>)。

 1. 當您在控制項或元件上使用方法時 (稱為「呼叫方法」)，需要新增括號。 因此，在 `ShowDialog` 中緊接 "g" 之後輸入左括弧和右括弧：`()`。現在這應該看起來像 "openFileDialog1.ShowDialog()"。

    > [!NOTE]
    > 方法是任何應用程式中很重要的一部分，而本教學課程已示範幾種使用方法的方法。 您可以呼叫元件的方法來指示元件執行動作，就像您呼叫 **OpenFileDialog** 元件的 `ShowDialog()` 方法一樣。 您可以建立自己的方法來讓您的應用程式執行作業，例如您現在所建立的方法，稱為 `showButton_Click()` 方法，這會在使用者選擇按鈕時開啟對話方塊和圖片。

 1. 若為 c #，請新增空格，然後將兩個等號 (`==`) 。 在 Visual Basic 中，新增空格，然後使用單一等號 (`=`)  (c # 和 Visual Basic 使用不同的等號比較運算子。 ) 

 1. 加入另一個空格。 這樣做之後，另一個 [IntelliSense] 視窗會隨即開啟。 開始鍵入 `DialogResult`，並選擇 **Tab** 鍵將其新增。

    > [!NOTE]
    > 當您撰寫程式碼來呼叫方法時，有時會傳回一個值。 在這個案例中，**OpenFileDialog** 元件的 <xref:System.Windows.Forms.CommonDialog.ShowDialog> 方法會傳回 <xref:System.Windows.Forms.DialogResult> 值。 DialogResult 是特殊值，可讓您得知對話方塊中發生的情形。 **OpenFileDialog** 元件可讓使用者選擇 [確定] 或 [取消]，因此其 `ShowDialog()` 方法會傳回 `DialogResult.OK` 或 `DialogResult.Cancel`。

 1. 鍵入一個點來開啟 DialogResult 值 [IntelliSense] 視窗。 輸入字母 `O`，然後選擇 **Tab** 鍵來插入 **OK**。

    若要深入了解 DialogResult，請參閱 [DialogResult](<xref:System.Windows.Forms.DialogResult>)。

    > [!NOTE]
    > 第一行程式碼應該就完成。 若為 c #，它應該如下所示。
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  在 Visual Basic 中，程式碼應該如下所示。
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. 現在再加入另一行程式碼。 您可以直接輸入它 (或複製並貼上)，但建議使用 IntelliSense 來加入它。 只要愈熟悉 IntelliSense，您自己撰寫程式碼的速度就會愈快。 最終的 `showButton_Click()` 方法看起來應該類似下列程式碼。

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb" id="Snippet1":::

## <a name="next-steps"></a>下一步

* 若要移至下一個教學課程步驟，請參閱 **[步驟9：檢查、批註及測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)**。

* 若要返回上一個教學課程步驟，請參閱[步驟 7：將對話方塊元件新增至您的表單](../ide/step-7-add-dialog-components-to-your-form.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
