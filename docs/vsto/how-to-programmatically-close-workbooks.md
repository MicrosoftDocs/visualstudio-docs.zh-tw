---
title: 'How to: Programmatically Close Workbooks | Microsoft Docs'
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
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: 52
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 4a769a2c60fba5e66091ecbfe731319da779e26a
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-close-workbooks"></a>How to: Programmatically Close Workbooks
  You can close the active workbook or you can specify a workbook to close.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="closing-the-active-workbook"></a>Closing the Active Workbook  
 There are two procedures for closing the active workbook: one for document-level customizations and one for VSTO Add-ins.  
  
#### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>To close the active workbook in a document-level customization  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> method to close the workbook associated with the customization. To use the following code example, run it in the `Sheet1` class in a document-level project for Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]  [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
#### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>To close the active workbook in a VSTO Add-in  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> method to close the active workbook. To use the following code example, run it in the `ThisAddIn` class in an VSTO Add-in project for Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="closing-a-workbook-that-you-specify-by-name"></a>Closing a Workbook That You Specify By Name  
 The way that you close a workbook that you specify by name is the same for VSTO Add-ins and document-level customizations.  
  
#### <a name="to-close-a-workbook-that-you-specify-by-name"></a>To close a workbook that you specify by name  
  
1.  Specify the workbook name as an argument to the <xref:Microsoft.Office.Interop.Excel.Workbooks> collection. The following code example assumes that a workbook named **NewWorkbook** is open in Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>See Also  
 [Working with Workbooks](../vsto/working-with-workbooks.md)   
 [How to: Programmatically Save Workbooks](../vsto/how-to-programmatically-save-workbooks.md)   
 [How to: Programmatically Open Workbooks](../vsto/how-to-programmatically-open-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)  
  
  
