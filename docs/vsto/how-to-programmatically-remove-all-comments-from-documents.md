---
title: "如何： 以程式設計方式從文件移除所有註解 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
ms.assetid: 920de39a-3b6d-4682-bca6-f4b4dedda1ac
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f22dd675cd6e247f2f6fd6c17f69ea6370230aa0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>如何：以程式設計方式從文件中移除所有的註解
  從 Microsoft Office Word 文件移除所有註解使用 DeleteAllComments 方法。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>從屬於文件層級自訂一部分的文件移除所有註解  
  
1.  呼叫您專案中之 <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> 類別的 `ThisDocument` 方法。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>使用 VSTO 增益集從文件移除所有註解  
  
1.  呼叫您要從中移除註解之 <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。  
  
     下列程式碼範例會從使用中文件移除所有註解。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式在文件中的文字加入註解](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)  
  
  