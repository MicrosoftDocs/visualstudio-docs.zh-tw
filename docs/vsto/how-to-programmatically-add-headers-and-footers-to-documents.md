---
title: 'How to: Programmatically Add Headers and Footers to Documents | Microsoft Docs'
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
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 552fbd6257589fe7a10012b80cb4f88696187b84
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>How to: Programmatically Add Headers and Footers to Documents
  You can add text to headers and footers in your document by using the <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> property and <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> property of the <xref:Microsoft.Office.Interop.Word.Section>. Each section of a document contains three headers and footers:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 The procedures are different for document-level customizations and VSTO Add-ins.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Document-Level Customizations  
 To use the following code examples, run them from the `ThisDocument` class in your project.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>To add text to footers in the document  
  
1.  The following code example sets the font of the text to be inserted into the primary footer of each section of the document, and then inserts text into the footer.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]  [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>To add text to headers in the document  
  
1.  The following code example adds a field to show the page number in each header in the document, and then sets the paragraph alignment so that the text aligns to the right of the header.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]  [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>VSTO Add-Ins  
 To use the following code examples, run them from the `ThisAddIn` class in your project.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>To add text to footers in a document  
  
1.  The following code example sets the font of the text to be inserted into the primary footer of each section of the document, and then inserts text into the footer. This code example uses the active document.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>To add text to headers in the document  
  
1.  The following code example adds a field to show the page number in each header in the document, and then sets the paragraph alignment so that the text aligns to the right of the header. This code example uses the active document.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>See Also  
 [How to: Programmatically Create New Documents](../vsto/how-to-programmatically-create-new-documents.md)   
 [How to: Programmatically Extend Ranges in Documents](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [How to: Programmatically Loop Through Found Items in Documents](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   
