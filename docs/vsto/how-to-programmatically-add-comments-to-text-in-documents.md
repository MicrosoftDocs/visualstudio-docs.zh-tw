---
title: "如何： 以程式設計方式在文件中的文字加入註解 |Microsoft 文件"
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
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
ms.assetid: 4e396e31-01bf-424c-be6b-9a1806bcd572
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 69f320ef3e7b3914d9d6eadb7466b3a216ef95d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>如何：以程式設計方式為文件中的文字加入註解
  文件類別的註解屬性中某個範圍的 Microsoft Office Word 文件中的文字加入註解。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例會將註解加入文件中的第一個段落。  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>若要在文件層級自訂中將新註解加入文字  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 方法，並提供範圍和註解文字。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>若要在 VSTO 增益集中將新註解加入文字  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 方法，並提供範圍和註解文字。  
  
     下列程式碼範例會將註解加入現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要變更 Word 加入註解中的使用者縮寫，請使用 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 屬性。  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式從文件移除所有註解](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Document 主項目](../vsto/document-host-item.md)  
  
  