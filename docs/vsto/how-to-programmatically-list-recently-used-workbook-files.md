---
title: 'How to: Programmatically List Recently Used Workbook Files | Microsoft Docs'
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
ms.assetid: 210a3753-4845-4875-b34a-a30d3a1299b3
caps.latest.revision: 42
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 44ae72b875f59edee7ae73f07e5ee77d42d9869f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>How to: Programmatically List Recently Used Workbook Files
  The <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> property returns a collection that contains the names of all the files that appear in the Microsoft Office Excel list of recently used files. The length of the list varies depending on the number of files the user has selected to retain. You can display the results in a range.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>To list recently used workbooks in a range object  
  
1.  Loop through the list of recent files and display the names in cells relative to a <xref:Microsoft.Office.Interop.Excel.Range> object.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>See Also  
 [Working with Workbooks](../vsto/working-with-workbooks.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
