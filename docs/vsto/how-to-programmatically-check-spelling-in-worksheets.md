---
title: 'How to: Programmatically Check Spelling in Worksheets | Microsoft Docs'
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
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
ms.assetid: 16367c5d-2075-4174-bb87-dfc59f02c84c
caps.latest.revision: 53
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 21a413a3e2d17d77fd83d5109587a96f323a0511
ms.openlocfilehash: dd554111613a6e5cf846d77a2747d2ad1af7a648
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>How to: Programmatically Check Spelling in Worksheets
  You can programmatically check the spelling of words in a worksheet. The **Spelling** dialog box automatically appears if there are any incorrectly spelled words in the worksheet.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>To check spelling in a worksheet in a document-level customization  
  
1.  Call the <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> method of the worksheet.  
  
     [!code-cs[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]  [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-an-vsto-add-in"></a>To check spelling in a worksheet in an VSTO Add-in  
  
1.  Call the <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> method of the active worksheet.  
  
     [!code-cs[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [How to: Programmatically Run Excel Calculations](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
