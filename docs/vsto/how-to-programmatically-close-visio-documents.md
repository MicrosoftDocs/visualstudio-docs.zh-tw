---
title: 'How to: Programmatically Close Visio Documents | Microsoft Docs'
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
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
ms.assetid: 59c0e215-a4c1-4b39-a491-37534f172705
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 5005047476f5622391f8a163d71e1f44394d7d7d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-close-visio-documents"></a>How to: Programmatically Close Visio Documents
  You can close the active Microsoft Office Visio document by using the Microsoft.Office.Interop.Visio.Document.Close method.  
  
 For details about this method, see the VBA reference documentation for the [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) method.  
  
## <a name="closing-the-active-document"></a>Closing the Active Document  
  
#### <a name="to-close-the-active-document"></a>To close the active document  
  
-   Call the Microsoft.Office.Interop.Visio.Document.Close method to close the active document.  
  
     To use the following code example, run it in the `ThisAddIn` class in an VSTO Add-in project for Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>See Also  
 [Visio Solutions](../vsto/visio-solutions.md)   
 [Visio Object Model Overview](../vsto/visio-object-model-overview.md)   
 [How to: Programmatically Create New Visio Documents](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [How to: Programmatically Open Visio Documents](../vsto/how-to-programmatically-open-visio-documents.md)   
 [How to: Programmatically Save Visio Documents](../vsto/how-to-programmatically-save-visio-documents.md)   
 [How to: Programmatically Print Visio Documents](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
