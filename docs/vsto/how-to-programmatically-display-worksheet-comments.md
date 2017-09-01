---
title: 'How to: Programmatically Display Worksheet Comments | Microsoft Docs'
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
- worksheets, comments
- comments, worksheets
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: 43
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: f2357066857982dfdc51731ed3f627a22304f2f1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-display-worksheet-comments"></a>How to: Programmatically Display Worksheet Comments
  You can programmatically show and hide comments in Microsoft Office Excel worksheets.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>To display all comments on a worksheet in a document-level customization  
  
1.  Set the <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> property to **true** if you want to show comments; otherwise **false**. This code must be placed in a sheet class, not in the `ThisWorkbook` class.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]  [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>To display all comments on a worksheet in an application-level VSTO Add-in  
  
1.  Set the <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> property to **true** if you want to show comments; otherwise **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Add and Delete Worksheet Comments](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)  
  
  
