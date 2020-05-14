---
title: 步驟 6：命名您的按鈕控制項
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579789"
---
# <a name="step-6-name-your-button-controls"></a>步驟 6：命名您的按鈕控制項

表單上只有一個 <xref:System.Windows.Forms.PictureBox>。 加入它時，IDE 會自動將它命名為 **pictureBox1**。 只有一個 <xref:System.Windows.Forms.CheckBox>，名稱為 **checkBox1**。 很快，您將編寫一些代碼，該代碼將引用 CheckBox 和圖片框。 由於每個控制項中只有一個，因此當您在代碼中看到**圖片Box1**或**checkBox1**時，您將知道這意味著什麼。

> [!TIP]
> 在 Visual Basic 中，任何控制項名稱的預設第一個字母都是大寫，所以是 **PictureBox1**、 **CheckBox1**，依此類推。

表單上有四個按鈕，IDE 將它們分別命名為 **button1**、 **button2**、 **button3**及 **button4**。 只從目前的名稱來看，並無法得知哪一個按鈕才是 [關閉] **** 按鈕，以及哪一個是 [顯示圖片] **** 按鈕。 這就是為按鈕控制項指定更具資訊性名稱會很有用的原因。

## <a name="to-name-your-button-controls"></a>命名您的按鈕控制項

1. 在表單上，選擇 [關閉] **** 按鈕。 （如果仍然選擇了所有按鈕，請選擇**Esc**鍵以取消選擇。在 **"屬性"** 視窗中滾動，直到看到 **（名稱）** 屬性。 （名稱 **）** 屬性在屬性按字母順序排列時靠近頂部。將名稱更改為**關閉Button**，如以下螢幕截圖所示。

    ![包含 closeButton 名稱的 [屬性] 視窗](../ide/media/express_setnameproperty.png)<br>*** ****具有****關閉按鈕****名稱*的屬性視窗

    > [!NOTE]
    > 嘗試更改按鈕的名稱以**關閉"按鈕**"，在"關閉"和"按鈕"兩個單詞之間有一個空格。 執行此操作時，IDE 將顯示一條錯誤訊息："屬性值無效。 控制項名稱中不允許空格 (和其他一些字元)。

1. 將其他三個按鈕分別重新命名為 **backgroundButton**、 **clearButton**和 **showButton**。
您可以選擇 [屬性] **** 視窗中的控制項選取器下拉式清單，以驗證這些名稱。 新按鈕名稱隨即出現。

1. 按兩下表單上的 [顯示圖片] **** 按鈕。 作為替代方法，請選擇表單上的 **"顯示圖片**"按鈕，然後按**Enter**鍵。 執行此操作時，IDE 將在名為**Form1.cs**的主視窗中打開一個附加選項卡。 （如果您使用的是視覺化基本，則選項卡名為**Form1.vb**。

   此選項卡顯示表單後面的代碼檔，如以下螢幕截圖所示。

    ![包含 Visual C&#35; 程式碼的 [Form1.cs] 索引標籤](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs****選項卡，帶有 C# 代碼*

    > [!NOTE]
    > 您的Form1.cs或 Form1.vb 選項卡可能會將 **"顯示按鈕"** 顯示為 **"顯示按鈕**"。

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

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   您正在查看名為`showButton_Click()`（或者， `ShowButton_Click()`） 的代碼。 當您開啟 **showButton** 按鈕的程式碼檔時，IDE 已將此加入至表單的程式碼。 在設計階段，當您開啟表單中的控制項程式碼檔案時，如果該控制項的程式碼不存在，會產生程式碼。 此代碼（稱為*方法*）在運行應用並選擇控制項時運行 - 在這種情況下，**請顯示圖片**按鈕。

1. 再次選擇**Windows 表單設計器**選項卡 **（Form1.cs [設計]），** 然後打開 **"清除圖片**"按鈕的代碼檔，在表單的代碼中為其創建方法。 針對其他兩個按鈕重複此步驟。 IDE 每一次都會將新的方法加入至表單的程式碼檔案。

1. 要再添加一種方法，請在**Windows 表單設計器**中打開**CheckBox**控制項的代碼檔，以使`checkBox1_CheckedChanged()`IDE 添加方法。 每當使用者選取或清除核取方塊時就會呼叫該方法。

   > [!TIP]
   > 處理應用時，您經常在代碼編輯器和**Windows 表單設計器**之間移動。 IDE 可讓您在專案中輕鬆巡覽。 使用**解決方案資源管理器**通過按兩下"視覺基礎"中的 C# 或*Form1.vb*中的*Form1.cs，* 或在功能表列上按一下"**查看** > **設計器**"，從而打開**Windows 表單設計器**。

    下列顯示您在程式碼編輯器中看到的新程式碼。

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > 您的代碼可能不會以"camelCase"字母顯示事件處理常式。

    您添加的五種方法稱為*事件處理常式*，因為每當發生事件（如使用者選擇按鈕或選擇框）時，應用程式都會調用它們。

    當您在設計階段於 IDE 檢視控制項的程式碼時，Visual Studio 會加入控制項的事件處理常式方法 (如果不存在)。 例如，當您按兩下按鈕時，IDE 會為其 <xref:System.Windows.Forms.Control.Click> 事件加入事件處理常式 (每當使用者選擇按鈕時，就會呼叫)。 當您按兩下核取方塊時，IDE 會為其 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件加入事件處理常式 (每當使用者選取或清除方塊時，就會呼叫)。

    為控制項加入事件處理常式之後，您隨時可以按兩下控制項，或是在功能表列上依序選擇 [檢視]**** > [程式碼]****，即可從 **Windows Forms 設計工具**回到此控制項。

    當您建置程式時，名稱很重要，而方法 (包括事件處理常式) 則可以具有您想要的任何名稱。 當您使用 IDE 加入事件處理常式時，IDE 會根據控制項的名稱和所處理的事件來建立名稱。

    例如，名為**showButton**的按鈕的 Click 事件稱為`showButton_Click()`（或者`ShowButton_Click()`） 事件處理常式方法。 此外，方法名稱後面通常會加上左括弧和右括弧 `()`，以表示目前所討論的是方法。

    如果您決定要更改代碼變數名稱，請按右鍵代碼中的變數，然後選擇**重構** > **重命名**。 會重新命名該變數在程式碼中的所有執行個體。 有關詳細資訊，請參閱[重命名重構](../ide/reference/rename.md)。

## <a name="next-steps"></a>後續步驟

* 要轉到下一個教程步驟，請參閱**[步驟 7：將對話方塊元件添加到表單](../ide/step-7-add-dialog-components-to-your-form.md)** 中。

* 要返回到前面的教程步驟，請參閱步驟[5：將控制項添加到表單](../ide/step-5-add-controls-to-your-form.md)中。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
