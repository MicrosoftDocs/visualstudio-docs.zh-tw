---
title: "逐步解說： 使用按鈕在工作表中的文字方塊中顯示文字 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b88940aa1329bc330e5d8bb7d114c21fac3dacb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>逐步解說：使用按鈕在工作表的文字方塊中顯示文字
  本逐步解說示範使用 Microsoft Office Excel 工作表，以及如何建立 Excel 專案中使用 Visual Studio 中的 Office 程式開發工具的按鈕和文字方塊的基本概念。 若要查看結果為已完成的範例，請參閱 Excel 控制項範例： [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在這個逐步解說期間，您將了解如何：  
  
-   將控制項加入工作表。  
  
-   按一下按鈕時填入文字方塊。  
  
-   測試您的專案。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="creating-the-project"></a>建立專案  
 在此步驟中，您將建立使用 Visual Studio 的 Excel 活頁簿專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立名稱的 Excel 活頁簿專案**我的 Excel 按鈕**。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新 Excel 活頁簿，並將**我的 Excel 按鈕**專案加入**方案總管 中**。  
  
## <a name="adding-controls-to-the-worksheet"></a>將控制項加入工作表  
 這個逐步解說中，您必須按鈕和第一個工作表上的文字方塊。  
  
#### <a name="to-add-a-button-and-a-text-box"></a>新增按鈕和文字方塊  
  
1.  確認**我的 Excel Button.xlsx**活頁簿是在 Visual Studio 設計工具中開啟與`Sheet1`顯示。  
  
2.  從**通用控制項** 索引標籤的 工具箱 拖曳<xref:Microsoft.Office.Tools.Excel.Controls.TextBox>至`Sheet1`。  
  
3.  從**檢視**功能表上，選取**屬性 視窗**。  
  
4.  確定**TextBox1**會顯示在**屬性**視窗下拉式方塊，並變更**名稱**文字方塊的屬性**displayText**.  
  
5.  拖曳**按鈕**控制項拖曳至`Sheet1`並變更下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**insertText**|  
    |**Text**|**插入文字**|  
  
 現在撰寫在按一下按鈕時執行的程式碼。  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>按一下按鈕時填入文字方塊  
 每次使用者按一下按鈕， **Hello World ！** 會附加到文字方塊中。  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>在按一下按鈕時寫入至文字方塊  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**Sheet1**，然後按一下 [**檢視程式碼**快顯功能表。  
  
2.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>按鈕的事件處理常式：  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  在 C# 中，您必須加入事件處理常式<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件，如下所示。 如需建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 您現在可以測試您的活頁簿，確定訊息**Hello World ！** 當您按一下按鈕時，會出現在文字方塊中。  
  
#### <a name="to-test-your-workbook"></a>測試您的活頁簿  
  
1.  請按 F5 執行您的專案。  
  
2.  按一下按鈕。  
  
3.  確認**Hello World ！** 會出現在文字方塊中。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範在 Excel 工作表上使用按鈕和文字方塊的基本概念。 接著可以執行下列一些工作：  
  
-   部署專案。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用核取方塊變更格式。 如需詳細資訊，請參閱[逐步解說： 變更工作表格式使用核取方塊控制項](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何： 將 Windows Form 控制項加入 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [使用 Excel 的逐步解說](../vsto/walkthroughs-using-excel.md)   
 [Office 文件上的 Windows Forms 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  