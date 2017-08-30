---
title: 'How to: Programmatically Run Excel Calculations | Microsoft Docs'
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
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
ms.assetid: 0bf30d93-8620-43ad-bfb8-f45bf3b5461f
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 21a413a3e2d17d77fd83d5109587a96f323a0511
ms.openlocfilehash: 5fc097b5f6036c6797bf3401923cdba27dc714f3
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-run-excel-calculations"></a>How to: Programmatically Run Excel Calculations  
  You use a similar process to run calculations in a <xref:Microsoft.Office.Tools.Excel.NamedRange> control or a native Excel range object.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="running-calculations-in-a-namedrange-control"></a>Running Calculations in a NamedRange Control  
 The following example creates a <xref:Microsoft.Office.Tools.Excel.NamedRange> at cell A1 and then calculates the cell. This code must be placed in a sheet class, not in the `ThisWorkbook` class.  
  
#### <a name="to-run-calculations-in-a-namedrange-control"></a>To run calculations in a NamedRange control  
  
1.  Create the named range.  
  
     [!code-cs[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]  [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]  
  
2.  Call the <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> method of the specified range.  
  
     [!code-cs[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]  [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]  
  
## <a name="running-calculations-in-a-native-excel-range"></a>Running Calculations in a Native Excel Range  
  
#### <a name="to-run-calculations-in-a-native-excel-range"></a>To run calculations in a native Excel Range  
  
1.  Create the named range.  
  
     [!code-cs[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]  
  
2.  Call the <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> method of the specified range.  
  
     [!code-cs[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]  
  
## <a name="see-also"></a>See Also  
 [Working with Ranges](../vsto/working-with-ranges.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
