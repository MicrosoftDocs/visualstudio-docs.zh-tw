---
title: 如何： 以程式設計方式列印工作表 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9d9bd4d28afb1eca2ff07a8847081864c7af5744
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-print-worksheets"></a>如何：以程式設計方式列印工作表
  您可以列印活頁簿中的任何工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>列印文件層級自訂的工作表  
  
#### <a name="to-print-a-worksheet"></a>列印工作表  
  
1.  呼叫 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> 方法，要求兩個複本，以及在列印前先預覽文件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>方法可讓您顯示在指定的物件**預覽列印**視窗。 下列程式碼假設您有名為 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。  
  
#### <a name="to-preview-a-page-before-printing"></a>在列印前先預覽頁面  
  
1.  呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>列印 VSTO 增益集的工作表  
  
#### <a name="to-print-a-worksheet"></a>列印工作表  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> 方法，要求兩個複本，以及在列印前先預覽文件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>方法可讓您顯示在指定的物件**預覽列印**視窗。  
  
#### <a name="to-preview-a-page-before-printing"></a>在列印前先預覽頁面  
  
1.  呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式檢查工作表拼字](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [工作表主項目](../vsto/worksheet-host-item.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  