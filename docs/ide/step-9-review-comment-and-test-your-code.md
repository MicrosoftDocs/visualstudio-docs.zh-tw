---
title: 步驟 9：檢閱、註解和測試您的程式碼
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
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
ms.openlocfilehash: 1b31532bf6c26512e471ee787dc7219620e6db62
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579753"
---
# <a name="step-9-review-comment-and-test-your-code"></a>步驟 9：檢閱、註解和測試您的程式碼

您接下來要將註解加入至程式碼。 注釋是一個注釋，不會更改應用的顯示方式。 它可讓讀取程式碼的人容易了解您的程式碼有何用途。 將註解加入至您的程式碼是個好習慣。

在 C# 中，兩個正向斜杠 （//） 將行標記為注釋。 在 Visual Basic 中，使用單引號 (') 將一行標示成註解。 添加注釋後，將測試應用程式。 較好的做法是，經常在您處理專案時執行和測試程式碼，以便在程式碼變得更複雜之前早期攔截並修正所有問題。 這稱為「反覆測試」**。

您剛才已建置一些有作用的功能，雖然尚未完成，但已能夠載入圖片。 在將註解加入至程式碼並測試之前，請花一點時間檢閱程式碼概念，因為您會經常用到這些概念：

- 當您在 **Windows Forms 設計工具**中按兩下 [顯示圖片]**** 按鈕時，IDE 會自動將*方法*新增至程式的程式碼。

- 方法是用來組織程式碼的方式，也就是將程式碼組合在一起的方式。

- 大多數時候，方法按特定循序執行少量操作，例如`showButton_Click()`（或`ShowButton_Click()`） 方法如何顯示對話方塊，然後載入圖片。

- 方法是由程式碼「陳述式」** 或程式碼行所構成。 可將方法視為將程式碼陳述式配套起來的機制。

- 執行 (或「呼叫」**) 方法時，會從第一個陳述式開始依序逐一執行方法中的陳述式。

   下列是陳述式的範例。

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   陳述式就是讓程式執行動作的機制。 在 C# 中，語句始終以分號結尾。 在 Visual Basic 中，行尾就代表陳述式結尾  （視覺基本版中不需要分號。前面的語句告訴控制項<xref:System.Windows.Forms.PictureBox>載入使用者使用**OpenFileDialog**元件選擇的檔。

## <a name="to-add-comments"></a>加入註解

1. 將下列註解加入至程式碼。

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]

     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    **showButton** 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式現在已完成，可以運作。 您已從 `if` 陳述式開始撰寫程式碼。 語句`if`是告訴應用"檢查這一件事，如果這是真的，請執行這些操作。 在這種情況下，您告訴你的應用打開 **"打開檔"** 對話方塊，如果使用者選擇檔並選擇 **"確定**"按鈕，請在**圖片盒**中載入該檔。

    > [!TIP]
    > 建置 IDE 可讓您輕鬆撰寫程式碼，而「程式碼片段」** 就是它基於此目的而提供的一種方式。 程式碼片段是捷徑，可展開成一小段程式碼區塊。
    >
    >  您可以看到所有可用的程式碼片段。 在功能表列上，選擇**工具** > **代碼程式碼片段管理器**。 對於 C#，`if`程式碼片段位於**Visual C#** 中。 對於`if`視覺化基本，程式碼片段位於**代碼模式** > **條件和迴圈中**。 您可以使用此管理員來瀏覽現有的程式碼片段或加入您自己的程式碼片段。
    >
    >  若要在輸入程式碼時啟動程式碼片段，請輸入程式碼並選擇 **Tab** 鍵。 許多程式碼片段會出現在 [IntelliSense]**** 視窗中，這就是為何選擇兩次 **Tab** 鍵的原因：第一次是從 [IntelliSense]**** 視窗中選取程式碼片段，第二次是指示 IDE 使用該程式碼片段。 (IntelliSense 支援 `if` 程式碼片段，但不支援 `ifelse` 程式碼片段)。

1. 在運行應用程式之前，請選擇"**全部保存"** 工具列按鈕來保存應用，該按鈕應類似于以下螢幕截圖。

     ![[全部儲存] 工具列按鈕](../ide/media/express_iconsaveall.png)<br>
***保存所有****按鈕*

     或者，要保存你的應用，請從功能表列中選擇 **"全部檔** > **保存**"（或按**Ctrl**+**Shift**+**S**）。 最好養成儘早並經常儲存的習慣。

     運行時，程式應類似于下圖。

     ![圖片檢視器](../ide/media/express_pictureviewerdonerun.png)<br>***圖片檢視器***

## <a name="to-test-your-app"></a>測試應用

1. 選擇**F5**鍵或選擇 **"開始調試**"工具列按鈕。

1. 選擇 [顯示圖片]**** 按鈕，執行您剛撰寫的程式碼。 首先，應用將打開 **"打開檔"** 對話方塊。 確認篩選出現在對話方塊底部的 [檔案類型]**** 下拉式清單中。 然後，瀏覽至圖片並開啟它。 在 [我的文件]** 資料夾的 [我的圖片\範例圖片]** 資料夾內，您通常可以找到 Windows 作業系統隨附的範例圖片。

    > [!TIP]
    > 如果未在 [選取圖片檔案]**** 對話方塊中看見任何影像，請確定已選取對話方塊右下方的下拉式清單中的 [所有檔案 (*.\*)]**** 篩選條件。

1. 載入圖片，而它會出現在 PictureBox 中。 然後藉由拖曳框線，嘗試調整表單大小。 因為您將 PictureBox 停駐在 TableLayoutPanel 內，而此面板本身又停駐在表單內，所以圖片區域會自行調整大小，成為與表單一樣寬，並填滿表單上方 90% 的空間。 這就是為何使用 <xref:System.Windows.Forms.TableLayoutPanel> 和 <xref:System.Windows.Forms.FlowLayoutPanel> 容器的原因：當使用者調整表單的大小時，這些容器可讓表單保持正確大小。

     就在此時，更大的圖片超過圖片檢視器的範圍框線。 在下一個步驟中，您會加入程式碼，將圖片調整為符合視窗大小。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 要轉到下一個教程步驟，請參閱**[步驟 10：編寫其他按鈕的代碼和核取方塊](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)**。

- 若要回到上一個教學課程步驟，請參閱[步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
