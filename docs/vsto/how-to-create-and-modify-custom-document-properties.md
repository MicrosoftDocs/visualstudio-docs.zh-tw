---
title: 'How to: Create and Modify Custom Document Properties | Microsoft Docs'
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
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
ms.assetid: 99d9dfaf-891f-4f3b-a580-67362afdaf34
caps.latest.revision: 47
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 3bf28426b348e5ac9f91021d0b74e2f60e7204b9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-create-and-modify-custom-document-properties"></a>How to: Create and Modify Custom Document Properties
  The Microsoft Office applications listed above provide built-in properties that are stored with documents. In addition, you can create and modify custom document properties if there is additional information you want to store with the document.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Use the CustomDocumentProperties property of a document to work with custom properties. For example, in a document-level project for Microsoft Office Excel, use the <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> property of the `ThisWorkbook` class. In a VSTO Add-in project for Excel, use the <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> property of a <xref:Microsoft.Office.Interop.Excel.Workbook> object. These properties return a <xref:Microsoft.Office.Core.DocumentProperties> object, which is a collection of <xref:Microsoft.Office.Core.DocumentProperty> objects. You can use the `Item` property of the collection to retrieve a particular property, either by name or by index within the collection.  
  
 The following example demonstrates how to add a custom property in a document-level customization for Excel and assign it a value.  
  
 ![link to video](../vsto/media/playvideo.gif "link to video") For a related video demonstration, see [How Do I: Access and Manipulate Custom Document Properties in Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Example  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)] [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Robust Programming  
 Attempting to access the `Value` property for undefined properties raises an exception.  
  
## <a name="see-also"></a>See Also  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)   
 [How to: Read from and Write to Document Properties](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  
