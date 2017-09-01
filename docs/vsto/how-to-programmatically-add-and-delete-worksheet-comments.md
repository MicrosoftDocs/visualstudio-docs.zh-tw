---
title: 'How to: Programmatically Add and Delete Worksheet Comments | Microsoft Docs'
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
- ranges, comments
- worksheets, comments
- comments, worksheets
ms.assetid: 3408ce22-a7b7-4e2b-bfc1-dc24d679ee73
caps.latest.revision: 53
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 8131a55cdc32b272a0dce5a1c7bfbcaf575b74bd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>How to: Programmatically Add and Delete Worksheet Comments
  You can programmatically add and delete comments in Microsoft Office Excel worksheets. Comments can be added only to single cells, not to multi-cell ranges.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="adding-and-deleting-a-comment-in-a-document-level-project"></a>Adding and Deleting a Comment in a Document-Level Project  
 The following examples assume that there is a single-cell <xref:Microsoft.Office.Tools.Excel.NamedRange> control named `dateComment` on a worksheet named `Sheet1`.  
  
#### <a name="to-add-a-new-comment-to-a-named-range"></a>To add a new comment to a named range  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> method of the <xref:Microsoft.Office.Tools.Excel.NamedRange> control and supply the comment text. This code must be placed in the `Sheet1` class.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]  [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>To delete a comment from a named range  
  
1.  Verify that a comment exists on the range and delete it. This code must be placed in the `Sheet1` class.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]  [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="adding-and-deleting-a-comment-in-an-vsto-add-in-project"></a>Adding and Deleting a Comment in an VSTO Add-in Project  
 The following examples assume that there is a single-cell <xref:Microsoft.Office.Interop.Excel.Range> named `dateComment` on the active worksheet.  
  
#### <a name="to-add-a-new-comment-to-an-excel-range"></a>To add a new comment to an Excel range  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> method of the <xref:Microsoft.Office.Interop.Excel.Range> and supply the comment text.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
#### <a name="to-delete-a-comment-from-an-excel-range"></a>To delete a comment from an Excel range  
  
1.  Verify that a comment exists on the range and delete it.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Display Worksheet Comments](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [NamedRange Control](../vsto/namedrange-control.md)  
  
  
