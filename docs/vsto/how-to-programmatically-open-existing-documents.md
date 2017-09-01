---
title: 'How to: Programmatically Open Existing Documents | Microsoft Docs'
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
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: a0078a0bde72abc94d586d22bdf4ef36c8b69801
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-open-existing-documents"></a>How to: Programmatically Open Existing Documents
  The <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> method opens the existing Microsoft Office Word document specified by a fully qualified path and file name. This method returns a <xref:Microsoft.Office.Interop.Word.Document> that represents the opened document.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-open-a-document"></a>To open a document  
  
-   Call the <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> method of the <xref:Microsoft.Office.Interop.Word.Documents> collection and supply a path to the document.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]  [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
### <a name="to-open-a-document-as-read-only"></a>To open a document as read-only  
  
-   Call the <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> method, supply a path to the document, and set the *ReadOnly* argument to **True** in the method call.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]  [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This code example requires the following:  
  
-   A document named NewDocument.doc must exist in a directory named Test on drive C.  
  
## <a name="see-also"></a>See Also  
 [How to: Programmatically Create New Documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [How to: Programmatically Close Documents](../vsto/how-to-programmatically-close-documents.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
