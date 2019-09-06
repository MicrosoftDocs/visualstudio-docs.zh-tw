---
title: 步驟 6：命名按鈕控制項
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 794244bcdb814f78338a119d27ec0b0299023e59
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293495"
---
# <a name="step-6-name-your-button-controls"></a>步驟 6：命名按鈕控制項

表單上只有一個 <xref:System.Windows.Forms.PictureBox>。 加入它時，IDE 會自動將它命名為 **pictureBox1**。 只有一個 <xref:System.Windows.Forms.CheckBox>，名稱為 **checkBox1**。 很快地，您會撰寫一些程式碼，而該程式碼會參考 CheckBox 和 PictureBox。 因為這些控制項都只有一個，所以當您在程式碼中看到**pictureBox1**或**checkBox1**時，就會知道其意義。

> [!TIP]
> 在 Visual Basic 中，任何控制項名稱的預設第一個字母都是大寫，所以是 **PictureBox1**、 **CheckBox1**，依此類推。

表單上有四個按鈕，IDE 將它們分別命名為 **button1**、 **button2**、 **button3**及 **button4**。 只從目前的名稱來看，並無法得知哪一個按鈕才是 [關閉] 按鈕，以及哪一個是 [顯示圖片] 按鈕。 這就是為按鈕控制項指定更具資訊性名稱會很有用的原因。

## <a name="to-name-your-button-controls"></a>命名您的按鈕控制項

1. 在表單上，選擇 [關閉] 按鈕。 (如果仍然已選取所有按鈕，請選擇 **Esc** 鍵取消選取)。在 [屬性] 視窗中捲動，直到看到 **(Name)** 屬性為止 (屬性依字母順序排列時， **(Name)** 屬性會靠近頂端)。將名稱變更為**closeButton**，如下列螢幕擷取畫面所示。

    ![包含 closeButton 名稱的 [屬性] 視窗](../ide/media/express_setnameproperty.png)<br>***屬性****具有的視窗****closeButton****名稱*

    > [!NOTE]
    > 嘗試將按鈕的名稱變更為 [關閉]**按鈕**，並在 [關閉] 和 [按鈕] 這兩個字之間加上空格。 當您這麼做時，IDE 會顯示錯誤訊息：「屬性值無效」。 控制項名稱中不允許空格 (和其他一些字元)。

1. 將其他三個按鈕分別重新命名為 **backgroundButton**、 **clearButton**和 **showButton**。
您可以選擇 [屬性] 視窗中的控制項選取器下拉式清單，以驗證這些名稱。 新按鈕名稱隨即出現。

1. 按兩下表單上的 [顯示圖片] 按鈕。 或者，選擇表單上的 [**顯示圖片**] 按鈕，然後按**enter**鍵。 當您這麼做時，IDE 會在主視窗中開啟另一個名為**Form1.cs**的索引標籤。 （如果您使用 Visual Basic，索引標籤**會命名為 form1.vb）。**

   此索引標籤會顯示表單後方的程式碼檔案，如下列螢幕擷取畫面所示。

    ![包含 Visual C&#35; 程式碼的 [Form1.cs] 索引標籤](../ide/media/express_showbuttoncode.png)<br>
*包含程式碼C#的*Form1.cs 索引標籤

    > [!NOTE]
    > 您的 [Form1.cs] 索引標籤可能會改為顯示**showButton**為**showButton** 。

1. 注意這部分程式碼。

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click
    
    End Sub
    ```

   > [!IMPORTANT]
   > 使用此頁面右上方的程式設計語言控制項，以查看C#程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

   您正在查看名`showButton_Click()`為的程式碼（ `ShowButton_Click()`也就是）。 當您開啟 **showButton** 按鈕的程式碼檔時，IDE 已將此加入至表單的程式碼。 在設計階段，當您開啟表單中的控制項程式碼檔案時，如果該控制項的程式碼不存在，會產生程式碼。 這個程式碼稱為 *「方法」* (method)，當您執行程式並選取控制項 (在此例中，[顯示圖片] 按鈕) 時執行它。

1. 再次選擇 [ **Windows Form 設計工具**] 索引標籤（ **[Form1.cs [Design]]** ），然後開啟 [**清除圖片**] 按鈕的程式碼檔，在表單的程式碼中建立其方法。 針對其他兩個按鈕重複此步驟。 IDE 每一次都會將新的方法加入至表單的程式碼檔案。

1. 若要再加入一個方法，在 [Windows Forms 設計工具] 中開啟 **CheckBox** 控制項的程式碼檔案，讓 IDE 加入 `checkBox1_CheckedChanged()` 方法。 每當使用者選取或清除核取方塊時就會呼叫該方法。

   > [!TIP]
   > 在設計程式時，您通常會在程式碼編輯器和 **Windows Forms 設計工具**之間移動。 IDE 可讓您在專案中輕鬆巡覽。 使用**方案總管**在 Visual Basic C#中*按兩下或 form1.vb 中的*[ *Form1.cs* ] 來開啟**Windows Form 設計工具**，或是在功能表列上選擇 [**視圖** > **設計**工具]。

    下列顯示您在程式碼編輯器中看到的新程式碼。

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]
    
    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    您加入的五個方法稱為「 *事件處理常式*」(Event Handler)，因為每當事件發生時 (例如使用者選擇按鈕或選取方塊)，程式就會呼叫這些方法。

    當您在設計階段於 IDE 檢視控制項的程式碼時，Visual Studio 會加入控制項的事件處理常式方法 (如果不存在)。 例如，當您按兩下按鈕時，IDE 會為其 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式 (每當使用者選擇按鈕時，就會呼叫)。 當您按兩下核取方塊時，IDE 會為其 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件加入事件處理常式 (每當使用者選取或清除方塊時，就會呼叫)。

    為控制項加入事件處理常式之後，您隨時可以按兩下控制項，或是在功能表列上依序選擇 [檢視] > [程式碼]，即可從 **Windows Forms 設計工具**回到此控制項。

    當您建置程式時，名稱很重要，而方法 (包括事件處理常式) 則可以具有您想要的任何名稱。 當您使用 IDE 加入事件處理常式時，IDE 會根據控制項的名稱和所處理的事件來建立名稱。

    例如，名為**showButton**之按鈕的 Click 事件稱為`showButton_Click()` （也`ShowButton_Click()`就是）事件處理常式方法。 此外，方法名稱後面通常會加上左括弧和右括弧 `()`，以表示目前所討論的是方法。

    如果您決定要變更程式碼變數名稱，請用滑鼠右鍵按一下程式碼中的變數，然後依序選擇 [重構] > [重新命名]。 會重新命名該變數在程式碼中的所有執行個體。 如需詳細資訊，請參閱[重新命名重構](../ide/reference/rename.md)。

## <a name="next-steps"></a>後續步驟

* 若要前往下一個教學課程步驟，請參閱[步驟 7：將對話方塊元件新增至表單](../ide/step-7-add-dialog-components-to-your-form.md)。

* 若要回到上一個教學課程步驟，請參閱[步驟 5：將控制項新增至表單](../ide/step-5-add-controls-to-your-form.md)。

## <a name="see-also"></a>另請參閱

* [教學課程 2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程 3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
