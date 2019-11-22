---
title: 步驟 5：將控制項新增至您的表單 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89ca4c02a1cbb1171619060b9478b5f2d3ccaa36
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295723"
---
# <a name="step-5-add-controls-to-your-form"></a>步驟 5：將控制項加入至您的表單
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在這個步驟中，您要將控制項 (例如 `PictureBox` 控制項和 `CheckBox` 控制項) 新增至表單。 接著，您要將按鈕加入至表單。

 ![影片連結](../data-tools/media/playvideo.gif "連結 playvideo")如需本主題的影片版本，請參閱[教學課程1：在 Visual Basic 中建立圖片檢視器-影片 2](https://go.microsoft.com/fwlink/?LinkId=205211)或[教學課程1：在C#影片2中建立圖片檢視器](https://go.microsoft.com/fwlink/?LinkId=205200)。 這些影片使用舊版 Visual Studio，因此有一些功能表命令以及某些使用者介面項目會有些微差異。 不過，概念和程序在目前 Visual Studio 版本中的運作方式雷同。

### <a name="to-add-controls-to-your-form"></a>若要將控制項加入至表單

1. 移至 [工具箱] 索引標籤 (位於 Visual Studio IDE 的左邊) 並展開 [通用控制項] 群組。 這樣會顯示您在表單上最常見的控制項。

2. 選擇表單上的 [TableLayoutPanel] 控制項。 若要確認已選取 TableLayoutPanel，請確定其名稱出現在 [屬性] 視窗上方的下拉式清單方塊中。 您也可以使用 [屬性] 視窗上方的下拉式清單方塊選擇表單控制項。 以這種方式選擇控制項通常比使用滑鼠選擇很小的控制項容易。

3. 按兩下 [**PictureBox**] 項目，將 PictureBox 控制項加入至表單。 由於 TableLayoutPanel 會停駐並填滿整個表單，因此 IDE 會將 PictureBox 控制項加入至第一個空白儲存格 (左上角)。

4. 選擇新的 PictureBox 控制項以選取該項目，然後選擇新的 PictureBox 控制項的黑色三角形顯示其工作清單，如下圖所示。

     ![PictureBox](../ide/media/express-pictureboxtasks.png "Express_PictureBoxTasks")工作PictureBox 工作

    > [!NOTE]
    > 如果不小心將錯誤類型的控制項加入至 TableLayoutPanel，您可以刪除它。 以滑鼠右鍵按一下控制項，然後在操作功能表中選擇 [刪除]。 您也可以使用功能表列移除表單中的控制項。 在功能表列上，選擇 [**編輯**]、[**復原**] 或 [**編輯**]、[**刪除**]。

5. 選擇 [**停駐於父容器中**] 連結。 這樣會自動將 PictureBox 的 [**Dock**] 屬性設定為 [**Fill**]。 若要確認這一點，請選擇 [PictureBox] 控制項選取它，然後移至 [**屬性**] 視窗並確定 [**Dock**] 屬性已設定為 [**Fill**]。

6. 變更 PictureBox 的 **ColumnSpan** 屬性，使 PictureBox 橫跨兩個資料行。 選擇 [PictureBox] 控制項，並將其 [**ColumnSpan**] 屬性設定為 [**2**]。 另外，您也想要在 PictureBox 空白時顯示空框架。 將其 [**BorderStyle**] 屬性設定為 [**Fixed3D**]。

    > [!NOTE]
    > 如果您未看見 PictureBox 的 [**ColumnSpan**] 屬性，可能是因為 PictureBox 是加入表單中，而不是 TableLayoutPanel。 若要修正這個問題，請選擇 [PictureBox]，將它刪除，選擇 [TableLayoutPanel]，然後加入新的 PictureBox。

7. 選擇表單上的 [TableLayoutPanel]，然後將 [**CheckBox**] 控制項加入至表單。 按兩下 [工具箱] 中的 [**CheckBox**] 項目，將新的 CheckBox 控制項加入至資料表中的下一個可用儲存格。 由於 PictureBox 會佔用 TableLayoutPanel 的前兩個儲存格，因此 CheckBox 控制項會加入至左下方儲存格。 選擇 [Text] 屬性，並輸入 **Stretch** 這個字，如下圖所示。

     ![具有 Stretch 屬性的 TextBox 控制項](../ide/media/express-pictureviewercheckbox.png "Express_PictureViewerCheckbox")具有 Stretch 屬性的 TextBox 控制項

8. 選擇表單上的 [TableLayoutPanel]，移至 [工具箱] 中的 [**容器**] 群組 (您取得 TableLayoutPanel 控制項的位置)，然後按兩下 [**FlowLayoutPanel**] 項目將新的控制項加入至 PictureBox (右下方) 中的最後一個儲存格。 接著將 FlowLayoutPanel 停駐在 TableLayoutPanel 中 (藉由選擇 FlowLayoutPanel 的黑色三角形工作清單上的 [停駐於父容器中]，或將 FlowLayoutPanel 的 [Dock] 屬性設定為 [Fill])。

    > [!NOTE]
    > FlowLayoutPanel 是一種容器，可依序整齊地排列其他控制項。 當您調整 FlowLayoutPanel 的大小時，如果還有空間可將所有控制項配置在單一資料列上，它就會這樣做。 否則，它會將控制項分行排列，由下往上堆疊控制項。 您將會使用 FlowLayoutPanel 來放置四個按鈕。 如果按鈕加入時為上下重疊排列，則務必在加入按鈕之前確定已選取 [FlowLayoutPanel]。 雖然先前表示每一個儲存格中只能有一個控制項，但是 TableLayoutPanel 的右下方儲存格中有四個按鈕控制項。 這是因為您可以在儲存格中放入一個控制項來存放其他控制項。 這類控制項稱為容器，而 FlowLayoutPanel 就是容器。

### <a name="to-add-buttons"></a>若要加入按鈕

1. 選擇您加入的新 FlowLayoutPanel。 移至 [工具箱] 中的 [**通用控制項**]，然後按兩下 [**Button**] 項目將稱為 [**button1**] 的按鈕控制項加入至 FlowLayoutPanel。 重複此步驟加入另一個按鈕。 IDE 判斷已有一個稱為 **button1** 的按鈕，所以會將下一個按鈕命名為 **button2**。

2. 您通常會使用 [工具箱] 加入其他按鈕。 此時，選擇 [**button2**]，然後在功能表列上選擇 [**編輯**]、[**複製**] (或按 Ctrl+C)。 在功能表列上選擇 [**編輯**]、[**貼上**] (或按 Ctrl+V)，貼上按鈕的複本。 現在再貼一次。 IDE 現在已將 [**button3**] 和 [**button4**] 加入至 FlowLayoutPanel。

    > [!NOTE]
    > 您可以複製及貼上任何控制項。 IDE 會以邏輯方式命名和放置新的控制項。 如果您將控制項貼至容器中，IDE 會選擇下一個邏輯放置空間。

3. 選擇第一個按鈕，將其 [Text] 屬性設定為 [顯示圖片]。 然後，將接下來三個按鈕的 [Text] 屬性分別設定為 [清除圖片]、[設定背景色彩] 和 [關閉]。

4. 下一個步驟是調整按鈕的大小和排列按鈕，使它們對齊面板右邊。 選擇 [FlowLayoutPanel] 並查看其 [**FlowDirection**] 屬性。 將此屬性設定為 [**RightToLeft**]。 這樣做之後，按鈕應該會立即對齊儲存格右邊，且順序會反轉，使得 [**顯示圖片**] 按鈕位於右邊。

    > [!NOTE]
    > 如果按鈕的順序還是不對，您可以在 FlowLayoutPanel 上拖曳按鈕，依任何順序重新排列按鈕。 您可以選擇按鈕並將它向左或向右拖曳。

5. 選擇 [關閉] 按鈕選取它。 按住 CTRL 鍵並選擇其他三個按鈕，將它們全部選取。 選取所有按鈕後，移至 [**屬性**] 視窗並向下捲動至 [**AutoSize**] 屬性。 此屬性會指示按鈕自動調整本身的大小，以容納其所有文字。 將此屬性設定為 [**true**]。 您的按鈕現在應該具有適當的大小且順序正確 （只要選取全部四個按鈕，您就可以同時變更所有四個**AutoSize**屬性）。下圖顯示四個按鈕。

     ![具有四個按鈕的圖片檢視器](../ide/media/express-autosize.png "Express_AutoSize")具有四個按鈕的圖片檢視器

6. 現在，重新執行程式來查看新配置的表單。 選擇按鈕和核取方塊並不會執行任何動作，不過很快就會有作用。

### <a name="to-continue-or-review"></a>繼續或檢視

- 若要移到下一個教學課程步驟，請參閱[步驟 6：命名您的按鈕控制項](../ide/step-6-name-your-button-controls.md)。

- 若要回到上一個教學課程步驟，請參閱[步驟 4：使用 TableLayoutPanel 控制項來配置您的表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。
