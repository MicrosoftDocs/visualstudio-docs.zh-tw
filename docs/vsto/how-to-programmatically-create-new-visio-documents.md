---
title: 'How to: Programmatically Create New Visio Documents | Microsoft Docs'
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
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: 22
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 65d5c2c857f8c859976e9964b866fa31fb2c912e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-create-new-visio-documents"></a>How to: Programmatically Create New Visio Documents
  When you create a new Microsoft Office Visio drawing document, you add it to the Microsoft.Office.Interop.Visio.Documents collection of open Visio documents. Consequently, the Microsoft.Office.Interop.Visio.Documents.Add method creates a new Visio drawing document. For more information, see the VBA reference documentation for the [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) method.  
  
## <a name="creating-new-blank-documents"></a>Creating New Blank Documents  
  
#### <a name="to-create-a-new-document"></a>To create a new document  
  
-   Use the Microsoft.Office.Interop.Visio.Documents.Add method to create a new blank document that is not based on a template.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Creating Documents Copied From Existing Documents  
 The Microsoft.Office.Interop.Visio.Documents.Add method can create a new document that is a copy of an existing Visio document. You must supply the file name and fully qualified path of the diagram.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>To create a new document that is copied from an existing document  
  
-   Call the Microsoft.Office.Interop.Visio.Documents.Add method and specify the path of the Visio diagram.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Creating Stencils Copied From Existing Stencils  
 The [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) method can create a new stencil that is a copy of an existing Visio stencil. You must supply the file name and fully qualified path of the stencil.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>To create a new stencil that is copied from an existing stencil  
  
-   Call the Microsoft.Office.Interop.Visio.Documents.Add method and specify the path of the stencil.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Creating Documents Based on Existing Templates  
 The Microsoft.Office.Interop.Visio.Documents.Add method can create a new document (a .vsd file) that is based on an existing Visio template (a .vst file). This method copies the stencils, styles, and settings that are part of the template workspace. You must supply the file name and fully qualified path of the template.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>To create a new document that is based on an existing template  
  
-   Call the Microsoft.Office.Interop.Visio.Documents.Add method and specify the path of the template.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]  [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This code example requires the following:  
  
-   A Visio document named `myDrawing.vsd` must be located in a directory named `Test` in the My Documents folder (for Windows XP and earlier) or the Documents folder (for Windows Vista).  
  
-   A Visio document named `myStencil.vss` must be located in a directory named `Test` in the My Documents folder (for Windows XP and earlier) or the Documents folder (for Windows Vista).  
  
-   A Visio document named `myTemplate.vst` must be located in a directory named `Test` in the My Documents folder (for Windows XP and earlier) or the Documents folder (for Windows Vista).  
  
## <a name="see-also"></a>See Also  
 [Visio Solutions](../vsto/visio-solutions.md)   
 [Visio Object Model Overview](../vsto/visio-object-model-overview.md)   
 [How to: Programmatically Open Visio Documents](../vsto/how-to-programmatically-open-visio-documents.md)   
 [How to: Programmatically Close Visio Documents](../vsto/how-to-programmatically-close-visio-documents.md)   
 [How to: Programmatically Save Visio Documents](../vsto/how-to-programmatically-save-visio-documents.md)   
 [How to: Programmatically Print Visio Documents](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
