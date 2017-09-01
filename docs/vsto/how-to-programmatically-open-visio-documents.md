---
title: 'How to: Programmatically Open Visio Documents | Microsoft Docs'
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
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
ms.assetid: bddb820c-bde7-4d21-a0b3-6d1968baccab
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 2cb8d4ef532d296b1bb750663d5650964d6d766b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-open-visio-documents"></a>How to: Programmatically Open Visio Documents
  There are two methods for opening existing Microsoft Office Visio documents: Open and OpenEx. The OpenEx method is identical to the Open method, except that it provides arguments in which the caller can specify how the document opens.  
  
 For details about the object model, see the VBA reference documentation for the [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) method and [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) method.  
  
## <a name="opening-a-visio-document"></a>Opening a Visio Document  
  
#### <a name="to-open-a-visio-document"></a>To open a Visio document  
  
-   Call the Microsoft.Office.Interop.Visio.Documents.Open method and supply the fully qualified path of the Visio document.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>Opening a Visio Document with Specified Arguments  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>To open a Visio document as read-only and docked  
  
-   Call the Microsoft.Office.Interop.Visio.Documents.OpenEx method, supply the fully qualified path of the Visio document, and include the arguments you want to use—in this case, Docked and Read-only.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This code example requires the following:  
  
-   A Visio document named `myDrawing.vsd` must be located in a directory named `Test` in the My Documents folder (for Windows XP and earlier) or the Documents folder (for Windows Vista).  
  
## <a name="see-also"></a>See Also  
 [Visio Solutions](../vsto/visio-solutions.md)   
 [Visio Object Model Overview](../vsto/visio-object-model-overview.md)   
 [How to: Programmatically Create New Visio Documents](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [How to: Programmatically Close Visio Documents](../vsto/how-to-programmatically-close-visio-documents.md)   
 [How to: Programmatically Save Visio Documents](../vsto/how-to-programmatically-save-visio-documents.md)   
 [How to: Programmatically Print Visio Documents](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
