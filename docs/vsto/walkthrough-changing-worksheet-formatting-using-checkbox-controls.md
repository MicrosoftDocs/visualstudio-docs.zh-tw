---
title: 使用 CheckBox 控制項變更工作表格式
description: 瞭解如何使用 Visual Studio 中的 Office 程式開發工具建立程式碼，並將其加入至您的專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 28b9f000c2e8517304387e2b203dfa7888b33d64
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527218"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>逐步解說：使用 CheckBox 控制項變更工作表格式
  本逐步解說會示範在 Microsoft Office Excel 工作表上使用核取方塊來變更格式的基本概念。 您將在 Visual Studio 中使用 Office 開發工具來建立程式碼，並將其新增至您的專案。 若要以完整範例的形式查看結果，請參閱 [Office 開發範例和](../vsto/office-development-samples-and-walkthroughs.md)逐步解說中的 Excel 控制項範例。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將文字和控制項加入工作表。

- 選取選項時將文字格式化。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在這個步驟中，您將使用 Visual Studio 建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立名稱為 **My Excel 格式** 的 Excel 活頁簿專案。 確定已選取 [ **建立新檔** ]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的 Excel 格式** ] 專案加入 **方案總管**。

## <a name="add-text-and-controls-to-the-worksheet"></a>將文字和控制項新增至工作表
 針對這個逐步解說，您將需要 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控制項中的三個控制項和一些文字 <xref:Microsoft.Office.Tools.Excel.NamedRange> 。

### <a name="to-add-three-check-boxes"></a>新增三個核取方塊

1. 確認活頁簿已在 Visual Studio 表設計工具中開啟，而且 `Sheet1` 已開啟。

2. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> 控制項拖曳至 **Sheet1** 中的或接近資料格 **B2** 。

3. 從 [ **View** ] 功能表選取 [ **屬性** 視窗]。

4. 確定 **Checkbox1** 顯示在 [ **屬性** ] 視窗的 [物件名稱] 清單方塊中，然後變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyBoldFont**|
    |**Text**|**粗體字**|

5. 拖曳第二個核取方塊，或接近儲存格 **B4** ，然後變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyItalicFont**|
    |**Text**|**斜體**|

6. 將第三個核取方塊拖曳到或附近的儲存格 **B6** ，然後變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyUnderlineFont**|
    |**Text**|**Underline**|

7. 按住 **Ctrl** 鍵同時選取全部三個核取方塊控制項。

8. 在 Excel 的 [格式] 索引標籤的 [排列] 群組中，按一下 [ **對齊**]，然後按一下 [靠 **左對齊**]。

     第三個核取方塊控制項在左側對齊您選取的第一個控制項的位置。

     接下來，您要將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳至工作表。

    > [!NOTE]
    > 您也可以在 <xref:Microsoft.Office.Tools.Excel.NamedRange> [**名稱**] 方塊中輸入 **textFont** 來新增控制項。

#### <a name="to-add-text-to-a-namedrange-control"></a>將文字加入至 NamedRange 控制項

1. 從 [工具箱] 的 [ **Excel 控制項** ] 索引標籤中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳至資料格 **B9**。

2. 確認 **$B $9** 出現在 [可編輯] 文字方塊中，且已選取 [ **B9** ] 儲存格。 如果不是，請按一下 [ **資料格]，然後** 選取它。

3. 按一下 [確定]。

4. 資料格 **B9** 會成為名為的範圍 `NamedRange1` 。

    工作表上沒有可見的指示，但 `NamedRange1` 會出現在 [**名稱**] 方塊中， (在選取 [資料格] 時， ) 左邊的工作表的正上方。

5. 確定 **NamedRange1** 顯示在 [ **屬性** ] 視窗的 [物件名稱] 清單方塊中，然後變更下列屬性：

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**textFont**|
   |**Value2**|**按一下核取方塊，即可變更此文字的格式。**|

   接下來，撰寫程式碼，以在選取選項時將文字格式化。

## <a name="format-the-text-when-an-option-is-selected"></a>選取選項時將文字格式化
 在本節中，您將撰寫程式碼，以便在使用者選取格式化選項時，變更工作表中的文字格式。

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>若要在選取核取方塊時變更格式

1. 在 [ **Sheet1**] 上按一下滑鼠右鍵，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyBoldFont` ：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyItalicFont` ：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> 核取方塊的事件處理常式 `applyUnderlineFont` ：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. 在 c # 中，您必須將核取方塊的事件處理常式加入至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試活頁簿，以確定當您選取或清除核取方塊時，文字的格式正確。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按 **F5** 執行您的專案。

2. 選取或清除核取方塊。

3. 確認文字的格式正確。

## <a name="next-steps"></a>後續步驟
 本逐步解說將說明在 Excel 工作表上使用核取方塊和格式化文字的基本概念。 接著可以執行下列一些工作：

- 部署專案。 如需詳細資訊，請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。
- 使用按鈕填入文字方塊。 如需詳細資訊，請參閱 [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。

## <a name="see-also"></a>另請參閱
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 檔上 Windows Forms 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
