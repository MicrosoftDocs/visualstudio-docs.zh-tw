---
title: 逐步解說：變更工作表的格式使用核取方塊控制項
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
ms.openlocfilehash: aba73d5fc6c1609a3347178765ba516840b5176e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061685"
---
# <a name="walkthrough-change-worksheet-formatting-using-checkbox-controls"></a>逐步解說：變更工作表的格式使用核取方塊控制項
  本逐步解說會示範使用 Microsoft Office Excel 工作表上的核取方塊變更格式的基本概念。 您將使用 Visual Studio 中的 Office 開發工具建立，並將程式碼新增至您的專案。 若要查看完整的範例結果，請參閱 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 您可以將文字和控制項加入工作表。

- 在選取的選項，請格式化的文字。

- 測試您的專案。

> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在此步驟中，您將使用 Visual Studio 中建立的 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立 Excel 活頁簿專案同名**我的 Excel 格式**。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的 Excel 格式設定**專案加入**方案總管 中**。

## <a name="add-text-and-controls-to-the-worksheet"></a>將文字和控制項加入工作表
 對於此逐步解說中，您需要三個<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控制項和某些文字<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。

### <a name="to-add-three-check-boxes"></a>若要新增三個核取方塊

1. 確認活頁簿 Visual Studio 設計工具中開啟`Sheet1`已開啟。

2. 從**通用控制項**索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控制項至或儲存格附近**B2**中**Sheet1**。

3. 從**檢視**功能表上，選取**屬性**視窗。

4. 務必**Checkbox1**中的物件名稱 清單方塊會顯示**屬性** 視窗中，並變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyBoldFont**|
    |**Text**|**粗體**|

5. 拖曳第二個核取方塊，開啟或儲存格附近**B4**並變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyItalicFont**|
    |**Text**|**斜體**|

6. 拖曳第三個核取方塊，開啟或儲存格附近**B6**並變更下列屬性：

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**applyUnderlineFont**|
    |**Text**|**加上底線**|

7. 選取所有的三個核取方塊控制項，同時保存**Ctrl**索引鍵。

8. 在 在 Excel 中的 格式 索引標籤的 排列 群組中，按一下**對齊**，然後按一下**靠左對齊**。

     三個核取方塊控制項對齊左邊，在您選取的第一個控制項的位置。

     接下來，您會將拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入工作表。

    > [!NOTE]
    >  您也可以加入<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項中輸入**textFont**成**名稱** 方塊中。

#### <a name="to-add-text-to-a-namedrange-control"></a>將文字加入 NamedRange 控制項

1. 從**Excel 控制項** 索引標籤的 工具箱 拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入儲存格**B9**。

2. 確認 **$B$ 9**會出現在可編輯的文字方塊中，且儲存格**B9**已選取。 如果沒有，請按一下資料格**B9**來選取它。

3. 按一下 [確定] 。

4. 儲存格**B9**成為名為範圍`NamedRange1`。

    沒有在工作表中的可見指示，但`NamedRange1`會出現在**名稱 方塊**（工作表上方左側） 當資料格**B9**已選取。

5. 務必**NamedRange1**中的物件名稱 清單方塊會顯示**屬性** 視窗中，並變更下列屬性：

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**textFont**|
   |**Value2**|**按一下核取方塊以變更這段文字格式。**|

   接下來，撰寫程式碼格式化的文字，在選取的選項。

## <a name="format-the-text-when-an-option-is-selected"></a>在選取的選項，格式化文字
 在本節中，您會撰寫程式碼，以便當使用者選取一個格式化選項，會變更的工作表中的文字格式。

### <a name="to-change-formatting-when-a-check-box-is-selected"></a>若要改變格式時核取方塊已選取

1. 以滑鼠右鍵按一下**Sheet1**，然後按一下**檢視程式碼**快顯功能表。

2. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyBoldFont`核取方塊：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]

3. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyItalicFont`核取方塊：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]

4. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyUnderlineFont`核取方塊：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]

5. 在 C# 中，您必須新增事件處理常式的核取方塊<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試您的活頁簿，藉此確定您選取或清除核取方塊時，文字會正確地格式化。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按下**F5**執行您的專案。

2. 選取或清除核取方塊。

3. 請確認文字的格式正確。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範使用核取方塊，並格式化文字在 Excel 工作表的基本概念。 接著可以執行下列一些工作：

- 部署專案。 如需詳細資訊，請參閱 <<c0> [ 藉由使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。
- 使用按鈕填入文字方塊。 如需詳細資訊，請參閱[逐步解說：使用按鈕在工作表中的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。

## <a name="see-also"></a>另請參閱
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 文件上的 Windows Form 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
