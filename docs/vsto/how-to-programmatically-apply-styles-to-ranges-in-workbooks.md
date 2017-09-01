---
title: 'How to: Programmatically Apply Styles to Ranges in Workbooks | Microsoft Docs'
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
- ranges, styles
- styles, workbook ranges
- workbooks, styles
ms.assetid: c7e781ed-f366-45bb-aeb6-69c10d19d842
caps.latest.revision: 51
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: a9eef108e1e7f7ecd1fc4197959ab9cce9ea6ad8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>How to: Programmatically Apply Styles to Ranges in Workbooks
  You can apply named styles to regions in workbooks. Excel supplies a number of predefined styles.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 The **Format Cells** dialog box displays all the options you can use to format cells, and each of these options is available from your code. To display this dialog box in Excel, click **Cells** on the **Format** menu.  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>To apply a style to a named range in a document-level customization  
  
1.  Create a new style and set its attributes.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]  [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]  
  
2.  Create a <xref:Microsoft.Office.Tools.Excel.NamedRange> control, assign text to it, and then apply the new style. This code must be placed in a sheet class, not in the `ThisWorkbook` class.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]  [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>To clear a style from a named range in a document-level customization  
  
1.  Apply the Normal style to the range. This code must be placed in a sheet class, not in the `ThisWorkbook` class.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]  [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]  
  
### <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>To apply a style to a named range in a VSTO Add-in  
  
1.  Create a new style and set its attributes.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]  
  
2.  Create a <xref:Microsoft.Office.Interop.Excel.Range>, assign text to it, and then apply the new style.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]  
  
### <a name="to-clear-a-style-from-a-named-range-in-an-vsto-add-in"></a>To clear a style from a named range in an VSTO Add-in  
  
1.  Apply the Normal style to the range.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]  [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]  
  
## <a name="see-also"></a>See Also  
 [Working with Ranges](../vsto/working-with-ranges.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
