---
title: Windows Form 設計工具教學課程
description: 瞭解如何使用 Windows Form 設計工具所提供的各種工具來建立應用程式。 應用程式是自訂控制項，它會使用許多可用的版面配置功能。
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 5803530290988affd6cfbb8342f3b1d545238985
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947842"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>教學課程：開始使用 Windows Form 設計工具

Windows Form 設計工具提供許多可用來建置 Windows Forms 應用程式的工具。 本文會說明如何使用由該設計工具所提供的各種工具來建置應用程式，包括執行下列工作：

- 使用對齊線來排列控制項。
- 使用智慧標籤來完成設計工具工作。
- 設定控制項的邊界和邊框距離。
- 使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來排列控制項。
- 使用 <xref:System.Windows.Forms.SplitContainer> 控制項來分割控制項的版面配置。
- 使用 [文件大綱] 視窗來瀏覽您的版面配置。
- 使用大小和位置資訊顯示來放置控制項。
- 使用 [屬性] 視窗來設定屬性值。

當您完成時，您將會有使用 Windows Form 設計工具所提供的許多版面配置功能組合而成的自訂控制項。 此控制項會實作簡易計算機的使用者介面 (UI)。 下列影像會顯示該簡易計算機的一般版面配置：

![導覽計算機 UI](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>建立自訂控制項專案

第一個步驟是建立 DemoCalculator 控制項專案。

1. 開啟 Visual Studio 並建立新的 [Windows Forms 控制項程式庫] 專案。 將專案命名為 **DemoCalculatorLib**。

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 中的 [Windows Forms 控制項程式庫] 範本](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. 若要重新命名檔案，請在 **方案總管** 中，以滑鼠右鍵按一下 [ **UserControl1** ] 或 [ **UserControl1.cs**]，選取 [ **重新命名**]，然後將檔案名變更為 DemoCalculator .vb 或 DemoCalculator.cs。 當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，請選取 [是]。

Windows Form 設計工具會顯示 DemoCalculator 控制項的設計工具介面。 在此檢視中，您可以從 [工具箱] 中選取控制項和元件，並將它們置於設計工具介面上，以圖形方式設計控制項的外觀。 如需自訂控制項的詳細資訊，請參閱[各種自訂控制項](/dotnet/framework/winforms/controls/varieties-of-custom-controls)。

## <a name="design-the-control-layout"></a>設計控制項版面配置

DemoCalculator 控制項包含數個 Windows Forms 控制項。 在此程序中，您將會使用 Windows Form 設計工具來排列控制項。

1. 在 Windows Form 設計工具中，選取右下角的大小調整控點並將它向右下方拖曳，來將 DemoCalculator 控制項變更成較大的大小。 在 Visual Studio 的右下角，找到該控制項的大小和位置資訊。 透過在調整控制項大小時觀察大小資訊，來將控制項的大小設定為 500 單位的寬度及 400 單位的高度。

2. 在 [工具箱] 中，選取 [容器] 節點來開啟它。 選取 **SplitContainer** 控制項並將它拖曳到設計工具介面。

   `SplitContainer` 會被置於 DemoCalculator 控制項的設計工具介面上。

    > [!TIP]
    > `SplitContainer` 能控制其本身的大小，以符合 DemoCalculator 控制項的大小。 查看 [屬性] 視窗以查看 `SplitContainer` 控制項的屬性設定。 尋找 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性。 它的值是 [DockStyle.Fill](xref:System.Windows.Forms.DockStyle.Fill)，這代表 `SplitContainer` 控制項一律會將其本身的大小調整為符合 DemoCalculator 控制項的界限。 調整 DemoCalculator 控制項的大小來驗證此行為。

3. 在 [屬性] 視窗中，將 <xref:System.Windows.Forms.SplitContainer.Dock%2A> 屬性的值變更為 `None`。

    `SplitContainer` 控制項會縮小為其預設大小，且不再遵循 DemoCalculator 控制項的大小。

4. 選取 `SplitContainer` 控制項右上角的智慧標籤字符 (![智慧標籤字符](media/smart-tag-glyph.gif))。 選取 [停駐於父容器中] 來將 `Dock` 屬性設定為 `Fill`。

    `SplitContainer` 控制項會固定到 DemoCalculator 控制項的界限。

    > [!NOTE]
    > 有數個控制項提供智慧標籤以協助設計。 如需詳細資訊，請參閱 [逐步解說：使用 Windows Forms 控制項上的智慧標籤執行一般](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls)工作。

5. 選取面板之間的垂直框線，並將其向右拖曳，如此一來，左方面板就會使用大部分的空間。

    `SplitContainer` 會將 DemoCalculator 控制項分割成兩個面板；這兩個面板之間會有可移動的框線。 左側的面板將會保存計算機按鈕和顯示，而右側的面板將會顯示使用者所執行算術運算的記錄。

6. 在 [屬性] 視窗中，將 `BorderStyle` 屬性的值變更為 `Fixed3D`。

7. 在 [工具箱] 中，選取 [通用控制項] 節點來開啟它。 選取 `ListView` 控制項並將它拖曳到 `SplitContainer` 控制項的右側面板。

8. 選取 `ListView` 控制項的智慧標籤字符。 在智慧標籤面板中，將 `View` 設定變更為 `Details`。

9. 在智慧標籤面板中，選取 [編輯資料行]。

   [ColumnHeader 集合編輯器] 對話方塊隨即開啟。

10. 在 [ColumnHeader 集合編輯器] 對話方塊中，選取 [新增] 以將資料行新增到 `ListView` 控制項。 將資料行 `Text` 屬性的值變更為 **History**。 選取 [確定] 以建立資料行。

11. 在智慧標籤面板中，選取 [停駐於父容器中]，然後選取智慧標籤字符以關閉智慧標籤面板。

12. 從 [工具箱] 中的 [容器] 節點，將 `TableLayoutPanel` 控制項拖曳到 `SplitContainer` 控制項的左側面板。

    `TableLayoutPanel` 控制項會出現在設計工具介面上，並開啟其智慧標籤面板。 `TableLayoutPanel` 控制項會以格線方式排列其子控制項。 `TableLayoutPanel` 控制項將會保存 DemoCalculator 控制項的顯示和按鈕。 如需詳細資訊，請參閱 [逐步解說：使用 TableLayoutPanel 排列控制項](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel)。

13. 選取智慧標籤面板上的 [編輯資料列與資料行]。

    [資料行和資料列樣式] 對話方塊隨即開啟。

14. 選取 [新增] 按鈕，直到畫面顯示五個資料行為止。 選取全部五個資料行，然後選取 [大小類型] 方塊中的 [百分比]。 將 [百分比] 值設定為 **20**。 這會將每個資料行設定為相同的寬度。

15. 在 [顯示] 底下，選取 [資料列]。

16. 選取 [新增]，直到顯示五個資料列為止。 選取全部五個資料列，然後選取 [大小類型] 方塊中的 [百分比]。 將 [百分比] 值設定為 **20**。 這會將每個資料列設定為相同的高度。

17. 選取 [確定] 以接受您的變更，然後選取智慧標籤字符來關閉智慧標籤面板。

18. 在 [屬性] 視窗中，將 `Dock` 屬性的值變更為 `Fill`。

## <a name="populate-the-control"></a>填入控制項

在設定控制項的版面配置之後，您現在便可以將按鈕和顯示填入 DemoCalculator 控制項中。

1. 在 [ **工具箱**] 中選取 `TextBox` 控制項圖示。

   系統會將 `TextBox` 控制項置於 `TableLayoutPanel` 控制項的第一個資料格中。

2. 在 [屬性] 視窗中，將 `TextBox` 控制項之 ColumnSpan 屬性的值變更為 **5**。

   `TextBox` 控制項會移至位於其資料列中央的位置。

3. 將 `TextBox` 控制項之 `Anchor` 屬性的值變更為 `Left`, `Right`。

   `TextBox` 控制項會水平展開以橫跨全部五個資料行。

4. 變更 `TextBox` 控制項的 `TextAlign` 屬性值為 `Right`。

5. 在 [屬性] 視窗中，展開 `Font` 屬性節點。 針對 `TextBox` 控制項，將 `Size` 設定為 **14**，然後將 `Bold` 設定為 **True**。

6. 選取 `TableLayoutPanel` 控制項。

7. 在 [ **工具箱**] 中選取 `Button` 圖示。

   系統會將 `Button` 控制項置於 `TableLayoutPanel` 控制項的下一個開放資料格中。

8. 在 [ **工具箱**] 中，選取 [ `Button` 圖示] 四次，以填入控制項的第二個數據列 `TableLayoutPanel` 。

9. 透過按住 **Shift** 鍵並選取全部五個 `Button` 控制項來全選它們。 按 **Ctrl** + **C** 將控制項複製 `Button` 到剪貼簿。

10. 按 **Ctrl** + **V** 三次，將控制項的複本貼 `Button` 到控制項的其餘資料列 `TableLayoutPanel` 。

11. 透過按住 **Shift** 鍵並選取全部 20 個 `Button` 控制項來全選它們。

12. 在 [屬性] 視窗中，將 `Dock` 屬性的值變更為 `Fill`。

    全部的 `Button` 控制項都會固定以填滿包含它們的資料格。

13. 在 [屬性] 視窗中，展開 `Margin` 屬性節點。 將 `All` 的值設定為 **5**。

    全部的 `Button` 控制項都會變小，以在彼此之間建立較大的邊界。

14. 選取 **button10** 和 **button20**，然後按 [刪除] 以將它們從版面配置中移除。

15. 選取 **button5** 和 **button15**，然後將其 `RowSpan` 屬性的值變更為 **2**。 它們將會成為 DemoCalculator 控制項的 [清除] 和 **=** 按鈕。

## <a name="use-the-document-outline-window"></a>使用 [文件大綱] 視窗

當您的控制項或表單被填入數個控制項時，可以使用 [文件大綱] 視窗來以較輕鬆的方式瀏覽您的版面配置。

1. 在功能表列上，選擇 [**查看**  >  **其他 Windows**  >  **檔大綱**]。

   [文件大綱] 視窗會顯示 DemoCalculator 控制項及組成它之控制項的樹狀檢視。 如 `SplitContainer` 等的容器控制項會將其子控制項顯示為樹狀中的子節點。 您也可以使用 [文件大綱] 視窗重新命名現有的控制項。

2. 在 [ **檔大綱** ] 視窗中，以滑鼠右鍵按一下 [ **button1**]，然後選取 [ **重新命名**]。 將其名稱變更為 sevenButton。

3. 使用 [文件大綱] 視窗，依照下列清單將 `Button` 控制項由設計工具產生的名稱變更為生產環境名稱：

   - 將 button1 變更為 **sevenButton**

   - 將 button2 變更為 **eightButton**

   - 將 button3 變更為 **nineButton**

   - 將 button4 變更為 **divisionButton**

   - 將 button5 變更為 **clearButton**

   - 將 button6 變更為 **fourButton**

   - 將 button7 變更為 **fiveButton**

   - 將 button8 變更為 **sixButton**

   - 將 button9 變更為 **multiplicationButton**

   - 將 button11 變更為 **oneButton**

   - 將 button12 變更為 **twoButton**

   - 將 button13 變更為 **threeButton**

   - 將 button14 變更為 **subtractionButton**

   - 將 button15 變更為 **equalsButton**

   - 將 button16 變更為 **zeroButton**

   - 將 button17 變更為 **changeSignButton**

   - 將 button18 變更為 **decimalButton**

   - 將 button19 變更為 **additionButton**

4. 使用 [文件大綱] 及 [屬性] 視窗，依照下列清單變更每個 `Button` 控制項名稱的 `Text` 屬性值：

   - 將 sevenButton 控制項文字屬性變更為 **7**

   - 將 eightButton 控制項文字屬性變更為 **8**

   - 將 nineButton 控制項文字屬性變更為 **9**

   - 將 divisionButton 控制項文字屬性變更為 **/** (正斜線) 

   - 將 clearButton 控制項文字屬性變更為 **清除**

   - 將 fourButton 控制項文字屬性變更為 **4**

   - 將 fiveButton 控制項文字屬性變更為 **5**

   - 將 sixButton 控制項文字屬性變更為 **6**

   - 將 multiplicationButton 控制項文字屬性變更為 **\*** (星號) 

   - 將 oneButton 控制項文字屬性變更為 **1**

   - 將 twoButton 控制項文字屬性變更為 **2**

   - 將 threeButton 控制項文字屬性變更為 **3**

   - 將 subtractionButton 控制項文字屬性變更為 **-** (連字號) 

   - 將 equalsButton 控制項文字屬性變更為 **=** (等號) 

   - 將 zeroButton 控制項文字屬性變更為 **0**

   - 將 changeSignButton 控制項文字屬性變更為 **+/-**

   - 將 decimalButton 控制項文字屬性變更為 **.** (句號)

   - 將 additionButton 控制項文字屬性變更為 **+** (加號) 

5. 在設計工具介面上，透過按住 **Shift** 鍵並選取全部的 `Button` 控制項來全選它們。

6. 在 [屬性] 視窗中，展開 `Font` 屬性節點。 針對所有 `Button` 控制項，將 `Size` 設定為 **14**，然後將 `Bold` 設定為 **True**。

這將能完成 DemoCalculator 控制項的設計。 剩下的工作便是提供計算機邏輯。

## <a name="implement-event-handlers"></a>實作事件處理常式

DemoCalculator 控制項上的按鈕具有事件處理常式，可用來實作大部分的計算機邏輯。 Windows Form 設計工具可讓您針對具有一個選取專案的所有按鈕，執行所有事件處理常式的存根。

1. 在設計工具介面上，透過按住 **Shift** 鍵並選取全部的 `Button` 控制項來全選它們。

2. 選取其中一個 `Button` 控制項。

   [程式碼編輯器] 將會開啟並顯示由設計工具所產生的事件處理常式。

## <a name="test-the-control"></a>測試控制項

由於 DemoCalculator 控制項是繼承自 <xref:System.Windows.Forms.UserControl> 類別，您可以使用 **UserControl 測試容器** 來測試它的行為。 如需詳細資訊，請參閱 [如何：測試 UserControl 的執行時間行為](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol)。

1. 按 **F5** 以在 [UserControl 測試容器] 中建置並執行 DemoCalculator 控制項。

2. 選取 `SplitContainer` 面板之間的框線，然後將它左右拖曳。 `TableLayoutPanel` 和其所有子控制項都會調整其本身的大小以符合可用空間。

3. 當您測試完控制項之後，請選取 [關閉]。

## <a name="use-the-control-on-a-form"></a>在表單上使用控制項

DemoCalculator 控制項可以用於其他複合控制項或是表單上。 下列程序說明它的使用方式。

### <a name="create-the-project"></a>建立專案

第一個步驟是建立應用程式專案。 您將會使用此專案來建置能顯示您自訂控制項的應用程式。

1. 建立新的 [Windows Forms 應用程式] 專案，然後將它命名為 **DemoCalculatorTest**。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 **DemoCalculatorTest** 專案，然後選取 [新增參考] 以開啟 [新增參考] 對話方塊。

3. 移至 [ **專案** ] 索引標籤，然後選取 [DemoCalculatorLib] 專案，以將參考加入至測試專案。

4. 在 [方案總管] 中，以滑鼠右鍵按一下 **DemoCalculatorTest**，然後選取 [設定為啟始專案]。

5. 在 [Windows Form 設計工具] 中，將表單的大小增加到大約為 **700 x 500**。

### <a name="use-the-control-in-the-forms-layout"></a>在表單的版面配置中使用控制項

若要在應用程式中使用 DemoCalculator 控制項，您必須將它置於表單上。

1. 在 [工具箱] 中，展開 [DemoCalculatorLib 元件] 節點。

2. 將 **DemoCalculator** 控制項從 [工具箱] 拖曳到您的表單上。 將控制項移至表單的左上角。 當控制項接近表單的框線時，畫面上將會出現「對齊線」。 對齊線會指出表單的 `Padding` 屬性和控制項的 `Margin` 屬性之間的距離。 將控制項置於對齊線所指示的位置。

   如需詳細資訊，請參閱 [逐步解說：使用對齊線排列控制項](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines)。

3. 從 [工具箱] 拖曳 `Button` 控制項，並將它置於表單上。

4. 在 DemoCalculator 控制項內四處移動 `Button` 控制項，並觀察對齊線的顯示位置。 您可以使用此功能來精確且輕鬆地對齊您的控制項。 當您完成時，請刪除 `Button` 控制項。

5. 以滑鼠右鍵按一下 [DemoCalculator] 控制項，然後選取 [ **屬性**]。

6. 將 `Dock` 屬性的值變更為 `Fill`。

7. 選取表單，然後展開 `Padding` 屬性節點。 將 **All** 的值變更為 **20**。

   DemoCalculator 控制項的大小會縮小以配合表單的新 `Padding` 值。

8. 透過將不同的大小調整控點拖曳到不同的位置來調整表單的大小。 觀察 DemoCalculator 控制項會如何調整大小來符合它。

## <a name="next-steps"></a>下一步

本文已示範如何建構簡易計算機的使用者介面。 若要繼續，您可以實作計算機邏輯來延伸其功能，然後[使用 ClickOnce 發佈應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。 或者，您可以繼續進行不同的教學課程並[使用 Windows Forms 建立圖片檢視器](../ide/tutorial-1-create-a-picture-viewer.md)。

## <a name="see-also"></a>另請參閱

- [Windows Forms 控制項](/dotnet/framework/winforms/controls/)
- [適用於 Windows Forms 控制項的協助工具](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [使用 ClickOnce 進行發佈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
