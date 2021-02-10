---
title: 步驟 5：將控制項新增至表單
description: 瞭解如何將控制項（例如 <xref:System.Windows.Forms.PictureBox> 控制項和 <xref:System.Windows.Forms.CheckBox> 控制項）新增至您的表單。
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58f46f80a90cce116b985def0377ef80f5a671c6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950662"
---
# <a name="step-5-add-controls-to-your-form"></a>步驟 5：將控制項新增至表單

在這個步驟中，您要將控制項 (例如 <xref:System.Windows.Forms.PictureBox> 控制項和 <xref:System.Windows.Forms.CheckBox> 控制項) 新增至表單。 然後將 <xref:System.Windows.Forms.Button> 控制項加入至表單。

## <a name="how-to-add-controls-to-your-form"></a>如何將控制項新增至表單

1. 選擇 Visual Studio IDE 左側的 [**工具箱**] 索引標籤 (或按 **Ctrl** + **Alt** + **X**) ，然後展開 [**通用控制項**] 群組。 這樣會顯示您在表單上最常見的控制項。

1. 按兩下 [PictureBox] 項目，將 PictureBox 控制項新增至表單。 由於 TableLayoutPanel 會停駐並填滿整個表單，因此 IDE 會將 PictureBox 控制項加入至第一個空白儲存格 (左上角)。

1. 選擇新的 **picturebox** 控制項來選取它，然後選擇新的 picturebox 控制項上的黑色三角形，以顯示其工作清單，如下列螢幕擷取畫面所示。

    ![PictureBox 工作](../ide/media/express_pictureboxtasks.png)<br/>PictureBox **_ _tasks**

    > [!NOTE]
    > 如果不小心將錯誤類型的控制項加入至 TableLayoutPanel，您可以刪除它。 以滑鼠右鍵按一下控制項，然後在操作功能表中選擇 [刪除]。 您也可以使用功能表列移除表單中的控制項。 在功能表列上，選擇 [**編輯**  >  **復原**] 或 [**編輯**  >  **刪除**]。

1. 在 **[picturebox] 控制項的**[ **picturebox** 工作] 功能表中，選擇 [停 **駐于父容器中**] 連結。 這樣會自動將 PictureBox 的 **Dock** 屬性設定為 **Fill**。 若要查看這一點，請選擇 [ **PictureBox** ] 控制項選取它，移至 [ **屬性** ] 視窗，並確定 [ **Dock** ] 屬性設定為 [ **填滿**]。

1. 變更 PictureBox 的 **ColumnSpan** 屬性，使 PictureBox 橫跨兩個資料行。 在 **picturebox** 中，選擇 [ **picturebox** ] 控制項，並將其 [ **ColumnSpan** ] 屬性設定為 [ **2**]。 另外，您也想要在 PictureBox 空白時顯示空框架。 將其 [BorderStyle] 屬性設定為 [Fixed3D]。

    > [!NOTE]
    > 如果您看不到 PictureBox 的 **ColumnSpan** 屬性，可能是因為 PictureBox 是新增至表單，而不是 TableLayoutPanel。 若要修正此問題，請選擇 **PictureBox**、將其刪除、選擇 **TableLayoutPanel**，然後加入新的 picturebox。

1. 選擇表單上的 [ **TableLayoutPanel** ]，然後將 [CheckBox] 控制項加入表單中。 按兩下 [**工具箱**] 中的 **核取方塊** 專案，將新的 checkbox 控制項新增至資料表中的下一個可用儲存格。 由於 PictureBox 會佔用 TableLayoutPanel 的前兩個儲存格，因此 CheckBox 控制項會加入至左下方儲存格。 選擇 [ **文字** ] 屬性，然後在 [自動 **延展**] 中輸入，如下圖所示。

    ![包含 Stretch 屬性的 TextBox 控制項](../ide/media/express_pictureviewercheckbox.png)<br/>***TextBox** _ _控制項與 * ***Stretch**_ _property *

1. 選擇表單上的 [ **TableLayoutPanel** ]，然後移至 [**工具箱**] 中的 [**容器**] 群組 (您取得 TableLayoutPanel 控制項的位置) 然後按兩下 [ **FlowLayoutPanel** ] 專案，將新的控制項加入至最後一個資料格 (右下方) 。 然後，將 FlowLayoutPanel 停駐在 TableLayoutPanel 中。 您可以選擇在 FlowLayoutPanel 的黑色三角形工作清單上的 [停 **駐于父容器中** ]，或將 FlowLayoutPanel 的 [ **dock** ] 屬性設定為 [ **填滿**]。

    > [!NOTE]
    > 是一種容器，可將資料 <xref:System.Windows.Forms.FlowLayoutPanel> 列中的其他控制項排列在一之後。 當您調整 FlowLayoutPanel 大小時，它會在單一資料列中配置所有的控制項（如果有空間的話）。 否則，它會將控制項分行排列，由下往上堆疊控制項。 <br/><br/>在這裡，您將使用 FlowLayoutPanel 來保存四個按鈕。 當您新增按鈕時，如果按鈕將其排列在上方，請務必先選取 FlowLayoutPanel，然後再新增按鈕。 <br/><br/> (通常，每個資料格都只會包含一個控制項。 在此範例中，TableLayoutPanel 的右下方儲存格包含四個按鈕控制項。 為什麼？  因為 FlowLayoutPanel 是容器控制項，所以會在保存其他控制項的資料格中擁有控制項。 ) 

## <a name="to-add-buttons"></a>若要加入按鈕

1. 選擇您加入的新 FlowLayoutPanel。 移至 [**工具箱**] 中的 [**通用控制項**]，然後按兩下 **按鈕** 專案，將名為 **button1** 的按鈕控制項新增至 FlowLayoutPanel。 重複此步驟加入另一個按鈕。 IDE 判斷已有一個稱為 **button1** 的按鈕，所以會將下一個按鈕命名為 **button2**。

1. 一般而言，您可以使用 [ **工具箱**] 加入其他按鈕。 這次選擇 [ **button2**]，然後從功能表列選擇 [**編輯**  >  **複製**] (或按 **Ctrl** + **C**) 。 接下來，從功能表列選擇 [**編輯**  >  **貼** 上] (或按 **Ctrl** + **V**) 貼上按鈕的複本。 現在再貼一次。 請注意，IDE 會將 **button3** 和 **Button4** 新增至 FlowLayoutPanel。

    > [!NOTE]
    > 您可以複製及貼上任何控制項。 IDE 會以邏輯方式命名和放置新的控制項。 如果您將控制項貼至容器中，IDE 會選擇下一個邏輯放置空間。

1. 選擇第一個按鈕，將其 [Text] 屬性設定為 [顯示圖片]。 然後，將接下來三個按鈕的 [Text] 屬性分別設定為 [清除圖片]、[設定背景色彩] 和 [關閉]。

1. 讓我們調整按鈕的大小並排列它們，使其對齊面板的右側。 選擇 [ **FlowLayoutPanel** ] 並查看其 **system.windows.frameworkelement.flowdirection** 屬性。 將此屬性設定為 [RightToLeft]。

   按鈕應該會將自己對齊到儲存格的右邊，並反轉順序，讓 [ **顯示圖片** ] 按鈕位於右邊。

    > [!NOTE]
    > 如果按鈕的順序還是不對，您可以在 FlowLayoutPanel 上拖曳按鈕，依任何順序重新排列按鈕。 您可以選擇按鈕並將它向左或向右拖曳。

1. 選擇 [關閉] 按鈕選取它。 然後，若要同時選擇其餘的按鈕，請按住 **Ctrl** 鍵並選擇它們。

   選取所有按鈕之後，請移至 [ **屬性** ] 視窗，並向上滾動至 [ **AutoSize** ] 屬性。 此屬性會指示按鈕自動調整本身的大小，以容納其所有文字。 將它設定為 **True**。

   您的按鈕現在應該具有適當的大小且順序正確   (只要選取了四個按鈕，您就可以同時變更全部四個 **AutoSize** 屬性。 ) 下圖顯示四個按鈕。

    ![包含四個按鈕的圖片檢視器](../ide/media/express_autosize.png)<br/>***圖片檢視器** _ _with 四個按鈕 *

1. 現在，再次執行程式以查看您的變更。

   請注意，按鈕和核取方塊並不會進行任何動作 &mdash; ，但很快就會進行。

## <a name="to-continue-or-review"></a>若要繼續或檢視

* 若要移至下一個教學課程步驟，請參閱 **[步驟6：命名您的按鈕控制項](../ide/step-6-name-your-button-controls.md)**。

* 若要回到上一個教學課程步驟，請參閱 [步驟4：使用 TableLayoutPanel 控制項配置您的表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
