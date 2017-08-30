---
title: 'How to: Programmatically Remove All Comments from Documents | Microsoft Docs'
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
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 315715e04ca6319a52e955442dcc141034752938
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>How to: Programmatically Remove All Comments from Documents
  Use the DeleteAllComments method to remove all comments from a Microsoft Office Word document.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>To remove all comments from a document that is part of a document-level customization  
  
1.  Call the <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> method of the `ThisDocument` class in your project. To use this code example, run it from the `ThisDocument` class.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]  [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>To remove all comments from a document by using an VSTO Add-in  
  
1.  Call the <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> method of the <xref:Microsoft.Office.Interop.Word.Document> from which you want to remove comments.  
  
     The following code example removes all comments from the active document. To use this code example, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>See Also  
 [How to: Programmatically Add Comments to Text in Documents](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Document Host Item](../vsto/document-host-item.md)  
  
  
