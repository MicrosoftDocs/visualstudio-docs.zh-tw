---
title: 如何：以程式設計方式將批註新增至檔中的文字
description: 以程式設計方式將批註新增至檔中的文字。 Document 類別的 [批註] 屬性會將批註新增至 Microsoft Word 檔中的文字範圍。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a39c02cfb7b170fd923e8e7409a0f4215d67583
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844591"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>如何：以程式設計方式將批註新增至檔中的文字
  Document 類別的 [批註] 屬性會將批註加入 Microsoft Office Word 檔中的文字範圍。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 下列範例會將註解加入文件中的第一個段落。

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>若要在文件層級自訂中將新註解加入文字

1. 呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> 方法，並提供範圍和註解文字。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>若要在 VSTO 增益集中將新批註加入至文字

1. 呼叫 <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> 屬性的 <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> 方法，並提供範圍和註解文字。

     下列程式碼範例會將註解加入現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>穩固程式設計
 若要變更 Word 加入註解中的使用者縮寫，請使用 <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> 屬性。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式從檔中移除所有批註](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [檔主專案](../vsto/document-host-item.md)
