---
title: 步驟 5：將控制項加入至您的表單
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579358"
---
# <a name="step-5-add-controls-to-your-form"></a>步驟 5：將控制項加入至您的表單

在這個步驟中，您要將控制項 (例如 <xref:System.Windows.Forms.PictureBox> 控制項和 <xref:System.Windows.Forms.CheckBox> 控制項) 新增至表單。 然後將 <xref:System.Windows.Forms.Button> 控制項加入至表單。

## <a name="how-to-add-controls-to-your-form"></a>如何向表單添加控制項

1. 選擇視覺化工作室 IDE 左側**的工具箱**選項卡（或按**Ctrl**+**Alt**+**X），** 然後展開 **"公共控制"** 組。 這樣會顯示您在表單上最常見的控制項。

1. 按兩下 [PictureBox]**** 項目，將 PictureBox 控制項新增至表單。 由於 TableLayoutPanel 會停駐並填滿整個表單，因此 IDE 會將 PictureBox 控制項加入至第一個空白儲存格 (左上角)。

1. 選擇新的**圖片框**控制項以選擇它，然後選擇新圖片盒控制項上的黑色三角形以顯示其工作清單，如下圖所示。

    ![PictureBox 工作](../ide/media/express_pictureboxtasks.png)<br/>圖片盒**任務**

    > [!NOTE]
    > 如果不小心將錯誤類型的控制項加入至 TableLayoutPanel，您可以刪除它。 以滑鼠右鍵按一下控制項，然後在操作功能表中選擇 [刪除]****。 您也可以使用功能表列移除表單中的控制項。 在功能表列上，選擇 **"編輯** > **撤銷"** 或 **"編輯** > **刪除**"。

1. 在 **"圖片盒**"控制項中的 **"圖片盒任務"** 功能表中，選擇**父容器連結中的停靠點**。 這樣會自動將 PictureBox 的 **Dock** 屬性設定為 **Fill**。 要查看這一點，請選擇 **"圖片框"** 控制項以選擇它，轉到 **"屬性"** 視窗，並確保**Dock**屬性設置為 **"填充**"。

1. 變更 PictureBox 的 **ColumnSpan** 屬性，使 PictureBox 橫跨兩個資料行。 在**圖片框**中，選擇 **"圖片框"** 控制項並將其**柱範圍**屬性設置為**2**。 另外，您也想要在 PictureBox 空白時顯示空框架。 將其 [BorderStyle]**** 屬性設定為 [Fixed3D]****。

    > [!NOTE]
    > 如果您看不到 PictureBox 的 **ColumnSpan** 屬性，可能是因為 PictureBox 是新增至表單，而不是 TableLayoutPanel。 要解決此問題，請選擇 **"圖片框**"，將其刪除，選擇 **"表格佈局面板**"，然後添加新的圖片盒。

1. 選擇表單上的 **"表佈局面板**"，然後將核取方塊控制項添加到表單中。 按兩下**工具箱**中的 **"核取方塊**"項，即可將新的核取方塊控制項添加到表中的下一個可用儲存格。 由於 PictureBox 會佔用 TableLayoutPanel 的前兩個儲存格，因此 CheckBox 控制項會加入至左下方儲存格。 選擇 **"文本"** 屬性並在"**拉伸"** 一詞中鍵入，如下圖所示。

    ![包含 Stretch 屬性的 TextBox 控制項](../ide/media/express_pictureviewercheckbox.png)<br/>*帶有****拉伸****屬性****的文字方塊***控制項

1. 選擇表單上的**表佈局面板**，然後轉到**工具箱**中的**容器**組（您得到了桌面面板控制項），然後按兩下**FlowLayoutPanel**項，將新控制項添加到最後一個儲存格（右下角）。 然後，在表佈局面板中停靠流佈局面板。 您可以通過在 FlowLayoutPanel 的黑三角形工作清單中選擇**父容器中的 Dock，** 或者通過將 FlowLayoutPanel 的**Dock**屬性設置為 **"填充**"來執行此操作。

    > [!NOTE]
    > A<xref:System.Windows.Forms.FlowLayoutPanel>是一個容器，用於一個接一個地排列一行中的其他控制項。 調整 FlowLayoutPanel 的大小時，如果有空間可以這樣做，它將在一行中列出其所有控制項。 否則，它會將控制項分行排列，由下往上堆疊控制項。 <br/><br/>在這裡，您將使用 FlowLayoutPanel 來容納四個按鈕。 如果添加按鈕時按鈕在另一個按鈕上排列，請確保在添加按鈕之前選擇 FlowLayoutPanel。 <br/><br/>（通常，每個儲存格只包含一個控制項。 在此示例中，表佈局面板的右下角儲存格包含四個按鈕控制項。 原因為何？  因為 FlowLayoutPanel 是一個容器控制項，它是儲存格中保存其他控制項的控制項。

## <a name="to-add-buttons"></a>若要加入按鈕

1. 選擇您加入的新 FlowLayoutPanel。 轉到**工具箱**中的 **"常見控制項**"，然後按兩下 **"按鈕**"項，將稱為按鈕**1**的按鈕控制項添加到 FlowLayoutPanel。 重複此步驟加入另一個按鈕。 IDE 判斷已有一個稱為 **button1** 的按鈕，所以會將下一個按鈕命名為 **button2**。

1. 通常，使用**工具箱**添加其他按鈕。 這一次，選擇**按鈕2，** 然後從功能表列，選擇**編輯** > **複製**（或按**Ctrl**+**C）。** 接下來，從功能表列中選擇 **"編輯** > **粘貼**"（或按**Ctrl**+**V**）以粘貼按鈕的副本。 現在再貼一次。 請注意，IDE 將**按鈕3**和**按鈕4**添加到 FlowLayout 面板中。

    > [!NOTE]
    > 您可以複製及貼上任何控制項。 IDE 會以邏輯方式命名和放置新的控制項。 如果您將控制項貼至容器中，IDE 會選擇下一個邏輯放置空間。

1. 選擇第一個按鈕，將其 [Text]**** 屬性設定為 [顯示圖片]****。 然後，將接下來三個按鈕的 [Text]**** 屬性分別設定為 [清除圖片]****、[設定背景色彩]**** 和 [關閉]****。

1. 讓我們調整按鈕的大小並排列它們，以便它們與面板的右側對齊。 選擇 **"流佈局面板**"並查看其**FlowDirection**屬性。 將此屬性設定為 [RightToLeft]****。

   按鈕應對齊到儲存格的右側，並反轉其順序，以便 **"顯示圖片**"按鈕位於右側。

    > [!NOTE]
    > 如果按鈕的順序還是不對，您可以在 FlowLayoutPanel 上拖曳按鈕，依任何順序重新排列按鈕。 您可以選擇按鈕並將它向左或向右拖曳。

1. 選擇 [關閉]**** 按鈕選取它。 然後，要同時選擇其餘按鈕，請按住**Ctrl**鍵並選擇它們。

   選擇所有按鈕後，轉到 **"屬性"** 視窗並向上滾動到 **"自動大小"** 屬性。 此屬性會指示按鈕自動調整本身的大小，以容納其所有文字。 將其設置為 **"真**"。

   您的按鈕現在應該具有適當的大小且順序正確  （只要選擇了所有四個按鈕，就可以同時更改所有四個**自動大小調整**屬性。下圖顯示了四個按鈕。

    ![包含四個按鈕的圖片檢視器](../ide/media/express_autosize.png)<br/>*帶四個按鈕****的圖片檢視器***

1. 現在再次運行程式以查看更改。

   請注意，按鈕和核取方塊尚未&mdash;執行任何操作，但它們很快就會執行。

## <a name="to-continue-or-review"></a>若要繼續或檢視

* 要轉到下一個教程步驟，請參閱**[步驟 6：命名按鈕控制項](../ide/step-6-name-your-button-controls.md)**。

* 要返回到前面的教程步驟，請參閱步驟[4：使用表佈局面板控制項佈局表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
