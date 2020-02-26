---
title: 步驟 4：使用 TableLayoutPanel 控制項來配置您的表單
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579377"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>步驟 4：使用 TableLayoutPanel 控制項來配置您的表單

在此步驟中，您會將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項新增至表單。 TableLayoutPanel 可協助適當地對齊您稍後將新增的表單中的控制項。

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>如何使用 TableLayoutPanel 控制項來配置表單

1. 在 Visual Studio IDE 的左側，選擇 [**工具箱**] 索引標籤。（或者，從功能表列選擇 [ **View** > **工具箱**]，或按**Ctrl**+**Alt**+**X**）。

1. 選擇 [**容器**] 群組旁的小三角形符號加以開啟，如下列螢幕擷取畫面所示。

     ![[容器] 群組](../ide/media/express_toolbox.png)<br>
***容器****群組*

1. 您可以將控制項 (例如按鈕、核取方塊和標籤) 加入至表單。 按兩下 [工具箱] 中的 TableLayoutPanel 控制項。 （或者，您可以將控制項從 [工具箱] 拖曳到表單上）。當您這麼做時，IDE 會將 TableLayoutPanel 控制項新增至您的表單，如下列螢幕擷取畫面所示。

     ![TableLayoutPanel 控制項](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel*** *控制項*

    > [!NOTE]
    > 新增 TableLayoutPanel 之後，如果表單內出現標題為 [TableLayoutPanel 工作] 的視窗，請選擇表單內的任何位置以關閉它。 稍後在本教學課程中，您將會進一步瞭解此視窗。

     請注意 [工具箱] 在您選擇索引標籤時會展開以包含您的表單，當您選擇其外部任何地方時就會關閉。 這是 IDE 中的 [自動隱藏] 功能。 您可以選擇視窗右上角的圖釘圖示，以開啟或關閉任何視窗，以切換自動隱藏並就地鎖定。 圖釘圖示顯示如下。

     ![圖釘圖示](../ide/media/express_pushpintoolbox.png)<br>
***圖釘****圖示*

1. 選擇 TableLayoutPanel 以確定選取它。 您可以查看 [**屬性**] 視窗頂端的下拉式清單，以驗證所選取的控制項，如下列螢幕擷取畫面所示。

     ![顯示 TableLayoutPanel 控制項的 [屬性] 視窗](../ide/media/express_controlspropwin.png)<br>
顯示***TableLayoutPanel*** *控制項*的 [***屬性*** *] 視窗*

1. 在 [屬性] 視窗的工具列上，選擇 [字母順序] 按鈕。 這會以字母順序排序 [**屬性**] 視窗中的屬性清單，讓您更輕鬆地在本教學課程中尋找屬性。

1. 控制項選取器是 [屬性] 視窗頂端的下拉式清單。 在此範例中，它顯示已選取一個稱為 `tableLayoutPanel1` 的控制項。 您可以從 **Windows Forms 設計工具**或從控制項選取器中選擇區域，即可選控制項。

   現在已選取 TableLayoutPanel ，請尋找 [停駐] 屬性並選擇 [停駐]，此屬性應該設定為 [無]。 請注意，值旁邊會出現下拉箭號。 選擇箭號，然後選取 [**填滿**] 按鈕（中間的大型按鈕），如下列螢幕擷取畫面所示。

     ![其中已選取 [Fill] 的 [屬性] 視窗](../ide/media/express_docktable.png)<br>
已*選取****填滿***的 [***屬性*** *] 視窗*

     Visual Studio 中的「停駐」是指在 IDE 中，將視窗附加至另一個視窗或區域。 例如，[**屬性**] 視窗可以是停駐&mdash;也就是未連結和自由浮動的 Visual Studio&mdash;，也可以停駐在**方案總管**上。

1. 將 [TableLayoutPanel **Dock** ] 屬性設定為 [ **Fill**] 之後，請注意面板會填滿整個表單。 如果您再次調整表單的大小，TableLayoutPanel 會停駐不動，並調整大小來填滿表單。

    > [!NOTE]
    > TableLayoutPanel 就像 Microsoft Office Word 中的表格 (具有列和欄)，且單一儲存格可以跨越多個列和欄。 每一個儲存格中放置一個控制項 (例如按鈕、核取方塊或標籤)。 您的 TableLayoutPanel 應該會有橫跨其整個頂端資料列的 <xref:System.Windows.Forms.PictureBox> 控制項、其左下方儲存格中的 <xref:System.Windows.Forms.CheckBox> 控制項，以及其右下方儲存格中的四個 <xref:System.Windows.Forms.Button> 控制項。

1. 目前，TableLayoutPanel 具有兩個大小相等的資料列和兩個大小相等的資料行。 讓我們將它們調整大小，讓上方的資料列和右邊的資料行變得更大。 在 **Windows Forms 設計工具**中，選取 [TableLayoutPanel]。 右上角有一個黑色的小型三角形按鈕，如下所示。

     ![三角形按鈕](../ide/media/express_iconblacktriangle.gif)<br>
***三角形****按鈕*

     此按鈕表示控制項具有可協助您自動設定其屬性的工作。

1. 選擇三角形以顯示控制項的 [工作清單]，如下列螢幕擷取畫面所示。

     ![TableLayoutPanel 工作](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel***工作

1. 選擇 [編輯資料列與資料行] 工作以顯示 [資料行和資料列樣式] 視窗。 選擇 [Column1]，記得要選取 [百分比] 按鈕，並在 [百分比] 方塊中輸入 **15**，即可將其大小設定為百分之 15。 （這是 <xref:System.Windows.Forms.NumericUpDown> 控制項，您將在稍後的教學課程中使用）。選擇 [ **Column2** ]，並將它設定為 [85%]。 還不要選擇 [確定] 按鈕，因為視窗將會關閉 （但是如果這樣做，您可以使用 [工作清單] 重新開啟它）。

     ![TableLayoutPanel 資料行和資料列樣式](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel***資料*行和資料列樣式*

1. 從 [資料**行和資料列樣式**] 視窗頂端的 [**顯示**] 下拉式清單中，**選擇 [** 資料列]。 將 [資料列 1] 設定為 90%，並將 [資料列 2] 設定為 10%。

1. 選擇 [確定] 按鈕。 TableLayoutPanel 現在應該具有大型的上方資料列、小型的下方資料列和大型的右邊資料行。 （您可以在表單中選擇 [ **tableLayoutPanel1** ]，然後拖曳其資料列和資料行框線），以調整 TableLayoutPanel 中的資料列和資料行大小。

     ![包含已調整大小之 TableLayoutPanel 的 Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
已調整大小之***TableLayoutPanel***的***Form1*** *（圖片檢視器）*

## <a name="next-steps"></a>後續步驟

* 若要移至下一個教學課程步驟，請參閱 **[步驟5：將控制項新增至表單](../ide/step-5-add-controls-to-your-form.md)** 。

* 若要回到上一個教學課程步驟，請參閱[步驟 3：設定您的表單屬性](../ide/step-3-set-your-form-properties.md)。

## <a name="see-also"></a>另請參閱

* [教學課程2：建立計時的數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教學課程3：建立配對遊戲](tutorial-3-create-a-matching-game.md)
