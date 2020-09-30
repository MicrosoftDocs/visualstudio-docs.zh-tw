---
title: 如何：以程式設計方式從檔中移除所有批註
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee30cb7d4083adfff18261e3267dea1d8a96626f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584816"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>如何：以程式設計方式從檔中移除所有批註
  您可以使用 `DeleteAllComments` 方法，從 Microsoft Office Word 文件移除所有註解。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>從屬於文件層級自訂一部分的文件移除所有註解

1. 呼叫您專案中之 <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> 類別的 `ThisDocument` 方法。 若要使用這個程式碼範例，請從 `ThisDocument` 類別執行程式碼。

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>使用 VSTO 增益集移除檔中的所有批註

1. 呼叫您要從中移除註解之 <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> 的 <xref:Microsoft.Office.Interop.Word.Document> 方法。

     下列程式碼範例會從使用中文件移除所有註解。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式將批註新增至檔中的文字](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [檔主專案](../vsto/document-host-item.md)
