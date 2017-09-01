---
title: 'How to: Programmatically Close Documents | Microsoft Docs'
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
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 0435e4cf7e8291fb893e8d1233e18e8fe7cd1c60
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-close-documents"></a>How to: Programmatically Close Documents
  You can close the active document or you can specify a document to close.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="closing-the-active-document"></a>Closing the Active Document  
 There are two procedures for closing the active document: one for document-level customizations and one for VSTO Add-ins.  
  
#### <a name="to-close-the-active-document-in-a-document-level-customization"></a>To close the active document in a document-level customization  
  
1.  Call the <xref:Microsoft.Office.Tools.Word.Document.Close%2A> method of the `ThisDocument` class in your project to close the document associated with the customization. To use the following code example, run it from the `ThisDocument` class.  
  
    > [!NOTE]  
    >  This example passes the <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> value to the *SaveChanges* parameter to close without saving changes or prompting the user.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]  [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
#### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>To close the active document in a VSTO Add-in  
  
1.  Call the <xref:Microsoft.Office.Interop.Word._Document.Close%2A> method of the <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> property to close the active document. To use the following code example, run it from the `ThisAddIn` class in your project.  
  
    > [!NOTE]  
    >  This example passes the <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> value to the *SaveChanges* parameter to close without saving changes or prompting the user.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="closing-a-document-that-you-specify-by-name"></a>Closing a Document That You Specify By Name  
 The way that you close a document that you specify by name is the same for VSTO Add-ins and document-level customizations.  
  
#### <a name="to-close-a-document-that-you-specify-by-name"></a>To close a document that you specify by name  
  
1.  Specify the document name as an argument to the <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> collection, and then call the <xref:Microsoft.Office.Interop.Word._Document.Close%2A> method. The following code example assumes that a document named **NewDocument** is open in Word.  
  
    > [!NOTE]  
    >  This example passes the <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> value to the *SaveChanges* parameter to close without saving changes or prompting the user.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]  [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>See Also  
 [How to: Programmatically Open Existing Documents](../vsto/how-to-programmatically-open-existing-documents.md)   
 [How to: Programmatically Save Documents](../vsto/how-to-programmatically-save-documents.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
