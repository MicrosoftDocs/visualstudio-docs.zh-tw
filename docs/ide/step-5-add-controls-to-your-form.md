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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579358"
---
# <a name="step-5-add-controls-to-your-form"></a>步驟 5：將控制項加入至您的表單

在這個步驟中，您要將控制項 (例如 <xref:System.Windows.Forms.PictureBox> 控制項和 <xref:System.Windows.Forms.CheckBox> 控制項) 新增至表單。 然後將 <xref:System.Windows.Forms.Button> 控制項加入至表單。

## <a name="how-to-add-controls-to-your-form"></a>如何將控制項新增至表單

1. 選擇 Visual Studio IDE 左側的 [**工具箱**] 索引標籤（或按**Ctrl**+**Alt**+**X**），然後展開 [**通用控制項**] 群組。 這樣會顯示您在表單上最常見的控制項。

1. 按兩下 [PictureBox] 項目，將 PictureBox 控制項新增至表單。 由於 TableLayoutPanel 會停駐並填滿整個表單，因此 IDE 會將 PictureBox 控制項加入至第一個空白儲存格 (左上角)。

1. 選擇新的**picturebox**控制項以選取它，然後選擇新的 picturebox 控制項上的黑色三角形來顯示其 [工作清單]，如下列螢幕擷取畫面所示。

    ![PictureBox 工作](../ide/media/express_pictureboxtasks.png)<br/>PictureBox ** * * 工作**

    > [!NOTE]
    > 如果不小心將錯誤類型的控制項加入至 TableLayoutPanel，您可以刪除它。 以滑鼠右鍵按一下控制項，然後在操作功能表中選擇 [刪除]。 您也可以使用功能表列移除表單中的控制項。 在功能表列上，依序選擇 [編輯] > [復原] 或 [編輯] > [刪除]。

1. 在**picturebox**控制項的 [ **picturebox**工作] 功能表中，選擇 [停**駐于父容器中**] 連結。 這樣會自動將 PictureBox 的 **Dock** 屬性設定為 **Fill**。 若要確認這一點，請選擇 **PictureBox** 控制項以選取該項目，並移至 [屬性] 視窗，然後確定 [Dock] 屬性設定為 [Fill]。

1. 變更 PictureBox 的 **ColumnSpan** 屬性，使 PictureBox 橫跨兩個資料行。 在**PictureBox**中，選擇 [ **picturebox** ] 控制項，並將其 [ **ColumnSpan** ] 屬性設定為 [ **2**]。 另外，您也想要在 PictureBox 空白時顯示空框架。 將其 [BorderStyle] 屬性設定為 [Fixed3D]。

    > [!NOTE]
    > 如果您看不到 PictureBox 的 **ColumnSpan** 屬性，可能是因為 PictureBox 是新增至表單，而不是 TableLayoutPanel。 若要修正這個問題，請選擇 [PictureBox]，將它刪除，選擇 [TableLayoutPanel]，然後加入新的 PictureBox。

1. 選擇表單上的 [TableLayoutPanel]，然後將 CheckBox 控制項新增至表單。 按兩下 [工具箱] 中的 **[CheckBox]** 項目，將新的 CheckBox 控制項新增至資料表的下一個可用儲存格。 由於 PictureBox 會佔用 TableLayoutPanel 的前兩個儲存格，因此 CheckBox 控制項會加入至左下方儲存格。 選擇 [ **Text** ] 屬性並輸入「 **Stretch**」，如下圖所示。

    ![包含 Stretch 屬性的 TextBox 控制項](../ide/media/express_pictureviewercheckbox.png)<br/>*具有* ***Stretch*** *屬性*的 TextBox 控制項

1. 選擇表單上的 [ **TableLayoutPanel** ]，然後移至 [**工具箱**] 中的 [**容器**] 群組（您擁有 TableLayoutPanel 控制項的位置），然後按兩下 [ **FlowLayoutPanel** ] 專案，將新的控制項加入最後一個資料格（右下方）。 然後，將 FlowLayoutPanel 停駐在 TableLayoutPanel 中。 若要這麼做，請在 FlowLayoutPanel 的黑色三角形工作清單上選擇 [停**駐于父容器中**]，或將 FlowLayoutPanel 的 [ **dock** ] 屬性設定為 [ **Fill**]。

    > [!NOTE]
    > 「<xref:System.Windows.Forms.FlowLayoutPanel>」是一種容器，會在資料列中逐一排列其他控制項。 當您調整 FlowLayoutPanel 大小時，它會在單一資料列中配置其所有控制項（如果它有空間可以這樣做）。 否則，它會將控制項分行排列，由下往上堆疊控制項。 <br/><br/>在這裡，您將使用 FlowLayoutPanel 來保存四個按鈕。 當您新增按鈕時，如果按鈕會在另一個上排列，請務必先選取 FlowLayoutPanel，然後再新增按鈕。 <br/><br/>（一般而言，每個資料格只會包含一個控制項。 在此範例中，TableLayoutPanel 的右下方資料格包含四個按鈕控制項。 原因為何？  因為 FlowLayoutPanel 是一個容器控制項，所以它是包含其他控制項之資料格中的控制項）。

## <a name="to-add-buttons"></a>若要加入按鈕

1. 選擇您加入的新 FlowLayoutPanel。 移至 [工具箱] 中的 [通用控制項]，然後按兩下 [Button] 項目，將稱為 **button1** 的按鈕控制項新增至 FlowLayoutPanel。 重複此步驟加入另一個按鈕。 IDE 判斷已有一個稱為 **button1** 的按鈕，所以會將下一個按鈕命名為 **button2**。

1. 一般而言，您可以使用 [**工具箱**] 加入其他按鈕。 這次請選擇  **button2**，然後從功能表列選擇 **編輯** > **複製** （或按**Ctrl**+**C**）。 接下來，從功能表列選擇 [**編輯** > **貼**上] （或按**Ctrl**+**V**）以貼上按鈕的複本。 現在再貼一次。 請注意，IDE 會將**button3**和**Button4**新增至 FlowLayoutPanel。

    > [!NOTE]
    > 您可以複製及貼上任何控制項。 IDE 會以邏輯方式命名和放置新的控制項。 如果您將控制項貼至容器中，IDE 會選擇下一個邏輯放置空間。

1. 選擇第一個按鈕，將其 [Text] 屬性設定為 [顯示圖片]。 然後，將接下來三個按鈕的 [Text] 屬性分別設定為 [清除圖片]、[設定背景色彩] 和 [關閉]。

1. 讓我們調整按鈕的大小並加以排列，使其對齊面板的右側。 選擇 [FlowLayoutPanel] 並查看其 [FlowDirection] 屬性。 將此屬性設定為 [RightToLeft]。

   按鈕應該對齊儲存格右邊，並反轉其順序，讓 [**顯示圖片**] 按鈕位於右邊。

    > [!NOTE]
    > 如果按鈕的順序還是不對，您可以在 FlowLayoutPanel 上拖曳按鈕，依任何順序重新排列按鈕。 您可以選擇按鈕並將它向左或向右拖曳。

1. 選擇 [關閉] 按鈕選取它。 然後，若要同時選擇其餘的按鈕，請按住**Ctrl**鍵並加以選擇。

   選取所有按鈕之後，請移至 [**屬性**] 視窗，並向上滾動至 [ **AutoSize** ] 屬性。 此屬性會指示按鈕自動調整本身的大小，以容納其所有文字。 將它設定為**True**。

   您的按鈕現在應該具有適當的大小且順序正確 （只要選取全部四個按鈕，您就可以同時變更所有四個**AutoSize**屬性）。下圖顯示四個按鈕。

    ![包含四個按鈕的圖片檢視器](../ide/media/express_autosize.png)<br/>*具有四個按鈕的****圖片檢視器***

1. 現在請再次執行您的程式，以查看您的變更。

   請注意，按鈕和核取方塊不會執行任何動作&mdash;但很快就會進行。

## <a name="to-continue-or-review"></a>繼續或檢視

* 若要移至下一個教學課程步驟，請參閱 **[步驟6：命名您的按鈕控制項](../ide/step-6-name-your-button-controls.md)** 。

* 若要回到上一個教學課程步驟，請參閱[步驟 4：使用 TableLayoutPanel 控制項來配置您的表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
