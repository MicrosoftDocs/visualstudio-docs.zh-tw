---
title: 'How to: Programmatically Print Worksheets | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
ms.assetid: 312bfcd7-0a74-421c-b42e-df71a06b7bdf
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 3253bb2fd9e434dfab39601f357aa175eb295a0b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-print-worksheets"></a>How to: Programmatically Print Worksheets
  You can print any worksheet in a workbook.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="printing-a-worksheet-in-a-document-level-customization"></a>Printing a Worksheet in a Document-Level Customization  
  
#### <a name="to-print-a-worksheet"></a>To print a worksheet  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> method of `Sheet1`, request two copies, and preview the document before printing.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]  [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
 The <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> method enables you to display the specified object in the **Print Preview** window. The following code assumes you have a <xref:Microsoft.Office.Tools.Excel.Worksheet> host item named `Sheet1`.  
  
#### <a name="to-preview-a-page-before-printing"></a>To preview a page before printing  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> method of the worksheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]  [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="printing-a-worksheet-in-a-vsto-add-in"></a>Printing a Worksheet in a VSTO Add-in  
  
#### <a name="to-print-a-worksheet"></a>To print a worksheet  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> method of the active worksheet, request two copies, and preview the document before printing.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
 The <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> method enables you to display the specified object in the **Print Preview** window.  
  
#### <a name="to-preview-a-page-before-printing"></a>To preview a page before printing  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> method of the active worksheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Check Spelling in Worksheets](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Worksheet Host Item](../vsto/worksheet-host-item.md)   
 [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
