---
title: 逐步解說： 變更工作表使用 CheckBox 控制項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35394b5f45e3c1e456dfcfae8f4b6db50af12147
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>逐步解說：使用 CheckBox 控制項來變更工作表格式
  本逐步解說示範使用 Microsoft Office Excel 工作表上的核取方塊變更格式的基本概念。 您將使用 Visual Studio 中的 Office 程式開發工具建立，並將程式碼加入至您的專案。 若要查看結果為已完成的範例，請參閱 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在這個逐步解說期間，您將了解如何：  
  
-   將文字和控制項加入工作表。  
  
-   在選取的選項，格式化的文字。  
  
-   測試您的專案。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>建立專案  
 在此步驟中，您將使用 Visual Studio 建立的 Excel 活頁簿專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立名稱的 Excel 活頁簿專案**我的 Excel 格式設定**。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新 Excel 活頁簿，並將**我的 Excel 格式設定**專案加入**方案總管 中**。  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>將文字和控制項加入至工作表  
 這個逐步解說中，您將需要三個<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控制項和某些文字<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。  
  
#### <a name="to-add-three-check-boxes"></a>若要加入三個核取方塊  
  
1.  確認活頁簿是在 Visual Studio 設計工具中，開啟`Sheet1`已開啟。  
  
2.  從**通用控制項** 索引標籤**工具箱**，拖曳<xref:Microsoft.Office.Tools.Excel.Controls.CheckBox>控制項或儲存格附近**B2**中**Sheet1**。  
  
3.  從**檢視**功能表上，選取**屬性**視窗。  
  
4.  確定**Checkbox1**會顯示在物件名稱 清單方塊的**屬性**視窗中，並變更下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**applyBoldFont**|  
    |**Text**|**粗體**|  
  
5.  拖曳第二個核取方塊，開啟或儲存格附近**B4**並變更下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**applyItalicFont**|  
    |**Text**|**斜體**|  
  
6.  拖曳第三個核取方塊，開啟或儲存格附近**B6**並變更下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**applyUnderlineFont**|  
    |**Text**|**底線**|  
  
7.  按住 CTRL 鍵同時選取所有的三個核取方塊控制項。  
  
8.  在 在 Excel 中的 格式 索引標籤的 排列 群組中，按一下**對齊**，然後按一下 **靠左對齊**。  
  
     三個核取方塊控制項對齊左邊，在您選取的第一個控制項的位置。  
  
     接下來，您會將<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入工作表。  
  
    > [!NOTE]  
    >  您也可以加入<xref:Microsoft.Office.Tools.Excel.NamedRange>輸入控制項**textFont**到**名稱**方塊。  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>將文字加入 NamedRange 控制項  
  
1.  從**Excel 控制項** 索引標籤的工具箱 拖曳<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入儲存格**B9**。  
  
2.  確認**$B$ 9**會出現在編輯的文字方塊和該資料格**B9**已選取。 如果沒有，請按一下資料格**B9**來選取它。  
  
3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  資料格**B9**成為具名範圍`NamedRange1`。  
  
     沒有可見指示工作表，但`NamedRange1`會出現在**名稱 方塊**（工作表上方左側） 當資料格**B9**已選取。  
  
5.  確定**NamedRange1**會顯示在物件名稱 清單方塊的**屬性**視窗中，並變更下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**textFont**|  
    |**Value2**|**按一下核取方塊變更格式，這段文字。**|  
  
 接下來，撰寫程式碼格式化的文字，在選取的選項。  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>已選取 自動格式化的文字時選項  
 在本節中，您將撰寫程式碼，如此當使用者選取一個格式化選項，會變更工作表中文字的格式。  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>若要變更格式時核取方塊已選取  
  
1.  以滑鼠右鍵按一下**Sheet1**，然後按一下 **檢視程式碼**快顯功能表。  
  
2.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyBoldFont`核取方塊：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyItalicFont`核取方塊：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式`applyUnderlineFont`核取方塊：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  在 C# 中，您必須加入事件處理常式的核取方塊，以<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試您的活頁簿，請確定您選取或清除核取方塊時，文字正確格式化。  
  
#### <a name="to-test-your-workbook"></a>測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  選取或清除核取方塊。  
  
3.  請確認文字會正確地格式化。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範使用核取方塊，與 Excel 工作表上的文字格式的基本概念。 接著可以執行下列一些工作：  
  
-   部署專案。 如需詳細資訊，請參閱[部署 Office 方案使用 clickonce](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
-   使用按鈕填入文字方塊。 如需詳細資訊，請參閱[逐步解說： 在工作表使用按鈕的文字方塊中顯示的文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 文件上的 Windows Forms 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  