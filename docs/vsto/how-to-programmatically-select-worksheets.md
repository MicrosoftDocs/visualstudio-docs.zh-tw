---
title: 'How to: Programmatically Select Worksheets | Microsoft Docs'
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
- worksheets, selecting
- Excel projects, selecting worksheets
ms.assetid: 9e7cdb11-e825-4c9f-abcd-d46fd20dc5e0
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 9330eb3deebcd7eb254b0f664b222566c29271b8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-select-worksheets"></a>How to: Programmatically Select Worksheets
  The <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> method selects the specified object, which moves the user's selection to the new object. Use the <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> method if you want to bring focus to the object without changing the user's selection.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 If you want to select an existing worksheet in a VSTO Add-in or if the worksheet was created at run time in a document-level customization, you must access it by using the Excel <xref:Microsoft.Office.Interop.Excel.Sheets> collection of the Excel workbook; otherwise, you can access the <xref:Microsoft.Office.Tools.Excel.Worksheet> host item directly.  
  
## <a name="using-the-worksheet-host-item"></a>Using the Worksheet Host Item  
 In a document-level customization, add the following code to **Sheet1.vb** or **Sheet1.cs**.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>To select the first worksheet in a workbook using a host item  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> method of `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]  [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Using the Sheets Collection of the Excel Workbook  
 Access the worksheet by using the Excel <xref:Microsoft.Office.Interop.Excel.Sheets> collection.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>To select the first worksheet in a workbook using the Sheets collection of the Excel workbook  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> method of the <xref:Microsoft.Office.Interop.Excel.Sheets> collection to select the first worksheet of the active workbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]  [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Print Worksheets](../vsto/how-to-programmatically-print-worksheets.md)   
 [How to: Programmatically Delete Worksheets from Workbooks](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [How to: Programmatically Hide Worksheets](../vsto/how-to-programmatically-hide-worksheets.md)   
 [How to: Programmatically Protect Worksheets](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Worksheet Host Item](../vsto/worksheet-host-item.md)   
 [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)  
  
  
