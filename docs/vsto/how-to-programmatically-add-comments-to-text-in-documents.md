---
title: HOW TO：以程式設計方式在文件中的文字中加入註解
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c5e7900f5316e64ef884d857bfc1448ac315fd19
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804600"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>HOW TO：以程式設計方式在文件中的文字中加入註解
  文件類別的註解屬性中某個範圍的 Microsoft Office Word 文件中的文字加入註解。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例會將註解加入文件中的第一個段落。  
  
## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>若要在文件層級自訂中將新註解加入文字  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 方法，並提供範圍和註解文字。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>將新的註解加入文字中的 VSTO 增益集  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 方法，並提供範圍和註解文字。  
  
     下列程式碼範例會將註解加入現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 若要變更 Word 加入註解中的使用者縮寫，請使用 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 屬性。  
  
## <a name="see-also"></a>另請參閱  
 [如何：以程式設計方式在文件中移除所有註解](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [文件主項目](../vsto/document-host-item.md)  
  
  