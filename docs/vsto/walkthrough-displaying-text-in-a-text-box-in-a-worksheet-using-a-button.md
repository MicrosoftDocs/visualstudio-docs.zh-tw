---
title: 逐步解說：在文字方塊中，使用按鈕在工作表中的顯示文字
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f74eaa8618ce497a760754d084f390a4d1b8c1d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436097"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>逐步解說：在文字方塊中，使用按鈕在工作表中的顯示文字
  本逐步解說會示範使用 Microsoft Office Excel 工作表，以及如何建立 Excel 專案在 Visual Studio 中使用 Office 開發工具的按鈕和文字方塊的基本概念。 若要查看完整的範例結果，請參閱 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將控制項加入工作表。

- 按一下按鈕時，請填入文字方塊。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

## <a name="create-the-project"></a>建立專案
 在此步驟中，您將建立使用 Visual Studio 的 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立 Excel 活頁簿專案同名**我的 [Excel] 按鈕**。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的 Excel 按鈕**專案加入**方案總管 中**。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 此逐步解說中，您將需要按鈕和第一個工作表上的文字方塊。

### <a name="to-add-a-button-and-a-text-box"></a>新增按鈕和文字方塊

1. 確認**我的 Excel Button.xlsx**活頁簿是在 Visual Studio 設計工具中開啟與`Sheet1`顯示。

2. 從**通用控制項** 索引標籤的 工具箱 拖曳<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>至`Sheet1`。

3. 從**檢視**功能表上，選取**屬性 視窗**。

4. 務必**TextBox1**會顯示在**屬性** 視窗的下拉式清單方塊，並變更**名稱**屬性的文字方塊中，以**3**.

5. 拖曳 **按鈕** 控制項拖曳至`Sheet1`並變更下列屬性：

   |屬性|值|
   |--------------|-----------|
   |**名稱**|**insertText**|
   |**Text**|**插入文字**|

   現在撰寫要在按下按鈕時執行的程式碼。

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>按一下按鈕時填入文字方塊
 每次使用者按一下按鈕， **Hello World ！** 會附加至文字方塊中。

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時寫入至文字方塊

1. 中**方案總管**，以滑鼠右鍵按一下**Sheet1**，然後按一下 **檢視程式碼**快顯功能表。

2. 將下列程式碼加入<xref:System.Windows.Forms.Control.Click>按鈕的事件處理常式：

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. 在 C# 中，您必須新增事件處理常式<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>測試應用程式
 您現在可以測試您的活頁簿，並確定訊息**Hello World ！** 當您按一下按鈕時，會出現在文字方塊中。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按下**F5**執行您的專案。

2. 按一下按鈕。

3. 確認**Hello World ！** 會出現在文字方塊中。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範在 Excel 工作表上使用按鈕和文字方塊的基本概念。 接著可以執行下列一些工作：

- 部署專案。 如需詳細資訊，請參閱 <<c0> [ 部署 Office 方案](../vsto/deploying-an-office-solution.md)。

- 使用核取方塊變更格式。 如需詳細資訊，請參閱[逐步解說：變更工作表使用核取方塊控制項的格式化](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。

## <a name="see-also"></a>另請參閱
- [如何：將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)
- [Office 文件上的 Windows Form 控制項的限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
