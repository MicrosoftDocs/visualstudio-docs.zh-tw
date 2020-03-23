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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579377"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>步驟 4：使用 TableLayoutPanel 控制項來配置您的表單

在此步驟中，您會將 <xref:System.Windows.Forms.TableLayoutPanel> 控制項新增至表單。 表佈局面板有助於在稍後添加的表單中正確對齊控制項。

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>如何使用表佈局面板控制項佈局表單

1. 在 Visual Studio IDE 的左側，選擇 **"工具箱**"選項卡。（或者，從功能表列中選擇 **"查看** > **工具箱**"，或按**Ctrl**+**Alt**+**X**.）

1. 選擇**容器**組旁邊的小三角形符號以將其打開，如下圖所示。

     ![[容器] 群組](../ide/media/express_toolbox.png)<br>
***容器****組*

1. 您可以將控制項 (例如按鈕、核取方塊和標籤) 加入至表單。 按兩下 [工具箱]**** 中的 TableLayoutPanel 控制項。 （或者，您可以將控制項從工具箱拖到表單上。執行此操作時，IDE 會向表單添加表佈局面板控制項，如下圖所示。

     ![TableLayoutPanel 控制項](../ide/media/express_formtablelayout.png)<br>
***表佈局面板****控制項*

    > [!NOTE]
    > 新增 TableLayoutPanel 之後，如果表單內出現標題為 [TableLayoutPanel 工作]**** 的視窗，請選擇表單內的任何位置以關閉它。 您將在本教程的後面部分瞭解有關此視窗的更多資訊。

     請注意 [工具箱]**** 在您選擇索引標籤時會展開以包含您的表單，當您選擇其外部任何地方時就會關閉。 這是 IDE 中的自動隱藏功能。 您可以通過選擇視窗右上角的圖釘圖示來切換"自動隱藏"並將其鎖定到位，從而打開或關閉任何視窗。 圖釘圖示顯示如下。

     ![圖釘圖示](../ide/media/express_pushpintoolbox.png)<br>
***圖釘****圖示*

1. 選擇 TableLayoutPanel 以確定選取它。 您可以通過查看 **"屬性"** 視窗頂部的下拉清單來驗證選擇哪些控制項，如下圖所示。

     ![顯示 TableLayoutPanel 控制項的 [屬性] 視窗](../ide/media/express_controlspropwin.png)<br>
*** ****顯示****表佈局面板****控制項*的屬性視窗

1. 在 [屬性]**** 視窗的工具列上，選擇 [字母順序]**** 按鈕。 這樣可以按字母順序對 **"屬性"** 視窗中的屬性清單進行排序，從而更輕鬆地在本教程中查找屬性。

1. 控制項選取器是 [屬性]**** 視窗頂端的下拉式清單。 在此範例中，它顯示已選取一個稱為 `tableLayoutPanel1` 的控制項。 您可以從 **Windows Forms 設計工具**或從控制項選取器中選擇區域，即可選控制項。

   現在已選取 TableLayoutPanel ，請尋找 [停駐]**** 屬性並選擇 [停駐]****，此屬性應該設定為 [無]****。 請注意，值旁邊會出現下拉箭號。 選擇箭頭，然後選擇 **"填充**"按鈕（中間的大按鈕），如下圖所示。

     ![其中已選取 [Fill] 的 [屬性] 視窗](../ide/media/express_docktable.png)<br>
*選擇****"填充"******的屬性****視窗*

     Visual Studio 中的「停駐」** 是指在 IDE 中，將視窗附加至另一個視窗或區域。 例如，"**屬性"** 視窗可以取消停靠&mdash;，即未附加和在 Visual Studio&mdash;中自由浮動，也可以停靠到**解決方案資源管理器**。

1. 將表佈局面板**停靠點**屬性設置為 **"填充**"後，請注意面板將填充整個表單。 如果您再次調整表單的大小，TableLayoutPanel 會停駐不動，並調整大小來填滿表單。

    > [!NOTE]
    > TableLayoutPanel 就像 Microsoft Office Word 中的表格 (具有列和欄)，且單一儲存格可以跨越多個列和欄。 每一個儲存格中放置一個控制項 (例如按鈕、核取方塊或標籤)。 表佈局面板應具有跨越其<xref:System.Windows.Forms.PictureBox>整個頂行的控制項、左下<xref:System.Windows.Forms.CheckBox>角儲存格中的控制項以及右下角儲存格中的四<xref:System.Windows.Forms.Button>個控制項。

1. 目前，TableLayoutPanel 具有兩個大小相等的資料列和兩個大小相等的資料行。 讓我們調整它們的大小，以便頂行和右列都大得多。 在 **Windows Forms 設計工具**中，選取 [TableLayoutPanel]。 右上角有一個黑色的小型三角形按鈕，如下所示。

     ![三角形按鈕](../ide/media/express_iconblacktriangle.gif)<br>
***三角形****按鈕*

     此按鈕表示控制項具有可協助您自動設定其屬性的工作。

1. 選擇三角形以顯示控制項的工作清單，如下圖所示。

     ![TableLayoutPanel 工作](../ide/media/express_tablepanel.png)<br>
***表佈局面板****任務*

1. 選擇 [編輯資料列與資料行]**** 工作以顯示 [資料行和資料列樣式]**** 視窗。 選擇 [Column1]****，記得要選取 [百分比]**** 按鈕，並在 [百分比]**** 方塊中輸入 **15**，即可將其大小設定為百分之 15。 （這是一個<xref:System.Windows.Forms.NumericUpDown>控制項，您將在後面的教程中使用。選擇**列 2**並將其設置為 85%。 還不要選擇 [確定]**** 按鈕，因為視窗將會關閉 （但是，如果您這樣做，則可以使用工作清單重新打開它。

     ![TableLayoutPanel 資料行和資料列樣式](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***表佈局面板****列和行樣式*

1. 從 **"列"和"行樣式"** 視窗頂部的 **"顯示**下拉清單"中，選擇 **"行**"。 將 [資料列 1]**** 設定為 90%，並將 [資料列 2]**** 設定為 10%。

1. 選擇 [確定] **** 按鈕。 TableLayoutPanel 現在應該具有大型的上方資料列、小型的下方資料列和大型的右邊資料行。 （您可以通過在表單中選擇**表LayoutPanel1，** 然後拖動其行和列邊框來調整表LayoutPanel中的行和列的大小。

     ![包含已調整大小之 TableLayoutPanel 的 Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
***表單 1（****圖片檢視器），帶調整大小的****桌面面板***

## <a name="next-steps"></a>後續步驟

* 要轉到下一個教程步驟，請參閱**[步驟 5：將控制項添加到表單](../ide/step-5-add-controls-to-your-form.md)** 中。

* 若要回到上一個教學課程步驟，請參閱[步驟 3：設定您的表單屬性](../ide/step-3-set-your-form-properties.md)。

## <a name="see-also"></a>另請參閱

* [教程 2：創建有時算數學測驗](tutorial-2-create-a-timed-math-quiz.md)
* [教程 3：創建匹配的遊戲](tutorial-3-create-a-matching-game.md)
