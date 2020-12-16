---
title: 如何：以程式設計方式定義和選取檔中的範圍
description: 瞭解如何使用 Range 物件，以程式設計方式定義和選取 Microsoft Word 檔中的範圍。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1cc0475f7b25550b85018477d7c842f012445e2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528322"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>如何：以程式設計方式定義和選取檔中的範圍
  您也可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件定義 Microsoft Office Word 文件中的範圍。 您可以使用數種方式來選取整份檔，例如，使用 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 物件的方法 <xref:Microsoft.Office.Interop.Word.Range> ，或使用 <xref:Microsoft.Office.Tools.Word.Document> 檔層級自訂) 中 (類別的 Content 屬性，或在 <xref:Microsoft.Office.Interop.Word.Document> VSTO 增益集) 中使用類別 (。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>定義範圍
 下列範例示範如何建立包含使用中文件中前七個字元 (包括非列印字元) 的新 <xref:Microsoft.Office.Interop.Word.Range> 物件。 它接著會選取範圍內的文字。

### <a name="to-define-a-range-in-a-document-level-customization"></a>定義文件層級自訂中的範圍

1. 將開始和結束字元傳遞給 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Range%2A> 方法，以將範圍新增至文件。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>使用 VSTO 增益集定義範圍

1. 將開始和結束字元傳遞給 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Range%2A> 方法，以將範圍新增至文件。 下列程式碼範例會將範圍新增至使用中文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>在檔層級自訂中選取範圍
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性來選取整份文件。

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>使用 Select 方法將整份文件選取為範圍

1. 使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>使用內容屬性將整份文件選取為範圍

1. 使用 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性定義包含整份文件的範圍。

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   您也可以使用其他物件的方法和屬性來定義範圍。

### <a name="to-select-a-sentence-in-the-active-document"></a>選取使用中文件中的句子

1. 使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。 使用您想要選取之句子的索引。

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   另一種選取句子的方法是手動設定範圍的開始和結束值。

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>手動設定開始和結束值來選取句子

1. 建立範圍變數。

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. 請檢查檔中是否至少有兩個句子，設定範圍的 *開始* 與 *結束* 引數，然後選取範圍。

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>使用 VSTO 增益集來選取範圍
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性來選取整份文件。

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>使用 Select 方法將整份文件選取為範圍

1. 使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 下列程式碼範例會選取使用中文件的內容。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>使用內容屬性將整份文件選取為範圍

1. 使用 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性定義包含整份文件的範圍。

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   您也可以使用其他物件的方法和屬性來定義範圍。

### <a name="to-select-a-sentence-in-the-active-document"></a>選取使用中文件中的句子

1. 使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。 使用您想要選取之句子的索引。

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   另一種選取句子的方法是手動設定範圍的開始和結束值。

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>手動設定開始和結束值來選取句子

1. 建立範圍變數。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. 請檢查檔中是否至少有兩個句子，設定範圍的 *開始* 與 *結束* 引數，然後選取範圍。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>另請參閱
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式取得範圍中的開始和結束字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式在 Word 檔中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式折迭檔中的範圍或選取專案](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
