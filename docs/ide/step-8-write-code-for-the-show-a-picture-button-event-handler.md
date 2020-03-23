---
title: 步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
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
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579801"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼

在此步驟中，使 **"顯示圖片**"按鈕的工作方式如下：

- 當使用者選擇該按鈕時，應用將打開一個<xref:System.Windows.Forms.OpenFileDialog>框。

- 如果使用者打開圖片檔，則應用將在 中顯示該<xref:System.Windows.Forms.PictureBox>圖片。

IDE 提供一個功能強大的工具，稱為 IntelliSense，可幫助您撰寫程式碼。 鍵入代碼時，IDE 將打開一個框，其中建議完成您輸入的部分單詞。

IntelliSense 嘗試確定您接下來要執行哪些操作，並自動跳轉到從清單中選擇的最後一個專案。 您可以利用向上或向下箭號在清單中移動，也可以繼續輸入字母來縮小選項範圍。 當您看到想要的選項時，選擇 **Tab** 鍵加以選取。 或者，如果不需要的話，您也可以忽略建議。

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>為顯示圖片按鈕事件處理常式撰寫程式碼

1. 移至 **Windows Forms 設計工具**，然後按兩下 [顯示圖片]**** 按鈕。 IDE 立即轉到代碼設計器並移動游標，使其位於之前添加的`showButton_Click()`（或者）`ShowButton_Click()`方法內。

1. 在兩個大括弧 `{ }` 之間的空白行上鍵入 `i` （在視覺化基本中，在`Private Sub...`和`End Sub`之間的空行上鍵入 。將打開 **"IntelliSense"** 視窗，如下圖所示。

    ![包含 Visual C&#35; 程式碼的 IntelliSense](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > 您的代碼可能不會以"camelCase"字母顯示事件處理常式。

1. **"IntelliSense"** 視窗應突出顯示該`if`單詞。 （如果沒有，請輸入小寫`f`，它將。請注意 **"IntelliSense"** 視窗旁邊的*工具提示*框如何與說明一起顯示，**如果語句的代碼程式碼片段**。 （在 Visual Basic 中，工具提示還指出這是一個片段，但措辭略有不同。您希望使用該程式碼片段，因此請選擇**Tab**鍵以插入`if`到代碼中。 然後再次選擇 **Tab** 鍵來使用 `if` 程式碼片段。 (如果您選擇其他位置並造成 [IntelliSense]**** 視窗消失，請按退格鍵刪除 `i` 並重新鍵入，[IntelliSense]**** 視窗就會再次開啟)。

    ![Visual C&#35; 程式碼](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>使用 IntelliSense 輸入更多代碼

接下來，您使用 IntelliSense 輸入更多程式碼，以開啟 [開啟檔案]**** 對話方塊。 如果使用者選擇 [確定]**** 按鈕，則 PictureBox 會載入使用者選取的檔案。 以下步驟演示如何輸入代碼，儘管有許多步驟，但只需幾下擊鍵：

 1. 從程式碼片段中選取的文字 **true** 開始。 鍵入 `op` 覆寫它 (在 Visual Basic 中，開頭是大寫，因此請鍵入 `Op`)。

 1. [IntelliSense]**** 視窗隨即開啟並顯示 [openFileDialog1]****。 選擇 **Tab** 鍵加以選取。 (在 Visual Basic 中，它的開頭是大寫，因此您會看到 [OpenFileDialog1]****。 確定已選取 [OpenFileDialog1]****)。

     若要深入了解 `OpenFileDialog`，請參閱 [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>)。

 1. 鍵入句點`.`（ （許多程式師稱之為點）。由於您在**打開 FileDialog1**後直接鍵入了一個點，因此將打開一個**IntelliSense**視窗，其中包含所有**OpenFileDialog**元件的屬性和方法。 當您在 **Windows Forms 設計工具**中選擇該元件時，[屬性]**** 視窗中也會顯示相同的屬性。 您也可以選擇指示元件執行動作 (例如開啟對話方塊) 的方法。

    > [!NOTE]
    > [IntelliSense]**** 視窗可以同時顯示屬性和方法。 若要判斷顯示的內容，請查看 [IntelliSense]**** 視窗中每個項目左方的圖示。 在每種方法旁邊可以看到一個塊的圖像，每個屬性旁邊都有扳手（或扳手）的圖像。 每一個事件旁邊也會出現閃電圖示。 <br><br>下面是顯示的圖示：<br><br>![方法圖示](../ide/media/express_iconmethod.png)<br>![屬性圖示](../ide/media/express_iconproperty.png)<br>![事件圖示](../ide/media/express_iconevent.png)

 1. 開始鍵入 `ShowDialog` (大小寫對 IntelliSense 而言不重要)。 `ShowDialog()` 方法會顯示 [開啟檔案]**** 對話方塊。 視窗反白顯示 **ShowDialog** 後，請選擇 **Tab** 鍵。 您也可以反白顯示 "ShowDialog" 並選擇 **F1** 鍵以取得其說明。

    若要深入了解 `ShowDialog()` 方法，請參閱 [ShowDialog 方法](<xref:System.Windows.Forms.Form.ShowDialog%2A>)。

 1. 當您在控制項或元件上使用方法時 (稱為「呼叫方法」**)，需要新增括號。 因此，在 `ShowDialog` 中緊接 "g" 之後輸入左括弧和右括弧：`()`。現在這應該看起來像 "openFileDialog1.ShowDialog()"。

    > [!NOTE]
    > 方法是任何應用的重要組成部分，本教程演示了幾種使用方法的方法。 您可以呼叫元件的方法來指示元件執行動作，就像您呼叫 **OpenFileDialog** 元件的 `ShowDialog()` 方法一樣。 您可以創建自己的方法，使應用執行操作操作，例如您現在構建的方法，稱為`showButton_Click()`方法，當使用者選擇按鈕時，該方法將打開對話方塊和圖片。

 1. 對於 C#，添加空格，然後添加兩個相等的符號`==`（ 。 在 Visual Basic 中，新增空格，然後使用單一等號 (`=`) （C# 和視覺化基本使用不同的相等運算子。

 1. 加入另一個空格。 這樣做之後，另一個 [IntelliSense]**** 視窗會隨即開啟。 開始鍵入 `DialogResult`，並選擇 **Tab** 鍵將其新增。

    > [!NOTE]
    > 當您撰寫程式碼來呼叫方法時，有時會傳回一個值。 在這個案例中，**OpenFileDialog** 元件的 <xref:System.Windows.Forms.CommonDialog.ShowDialog> 方法會傳回 <xref:System.Windows.Forms.DialogResult> 值。 DialogResult 是特殊值，可讓您得知對話方塊中發生的情形。 **OpenFileDialog** 元件可讓使用者選擇 [確定]**** 或 [取消]****，因此其 `ShowDialog()` 方法會傳回 `DialogResult.OK` 或 `DialogResult.Cancel`。

 1. 鍵入一個點來開啟 DialogResult 值 [IntelliSense]**** 視窗。 輸入字母 `O`，然後選擇 **Tab** 鍵來插入 **OK**。

    若要深入了解 DialogResult，請參閱 [DialogResult](<xref:System.Windows.Forms.DialogResult>)。

    > [!NOTE]
    > 第一行程式碼應該就完成。 對於 C#，它應該類似于以下內容。
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  在 Visual Basic 中，程式碼應該如下所示。
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. 現在再加入另一行程式碼。 您可以直接輸入它 (或複製並貼上)，但建議使用 IntelliSense 來加入它。 只要愈熟悉 IntelliSense，您自己撰寫程式碼的速度就會愈快。 最終`showButton_Click()`方法應類似于以下代碼。

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>後續步驟

* 要轉到下一個教程步驟，請參閱**[步驟 9：審閱、注釋和測試代碼](../ide/step-9-review-comment-and-test-your-code.md)**。

* 若要返回上一個教學課程步驟，請參閱[步驟 7：將對話方塊元件新增至您的表單](../ide/step-7-add-dialog-components-to-your-form.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
