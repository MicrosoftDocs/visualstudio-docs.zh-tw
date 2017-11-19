---
title: "如何： 以程式設計方式定義及選取範圍中的文件 |Microsoft 文件"
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
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fcc1b96607c36fdfbc2f9940a7b7984b3b299fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>如何：以程式設計方式在文件中定義及選取範圍
  您也可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件定義 Microsoft Office Word 文件中的範圍。 您可以選取數種方式，將整個文件，例如使用<xref:Microsoft.Office.Interop.Word.Range.Select%2A>方法<xref:Microsoft.Office.Interop.Word.Range>物件，或使用的內容屬性<xref:Microsoft.Office.Tools.Word.Document>類別 （在文件層級自訂） 或<xref:Microsoft.Office.Interop.Word.Document>類別 (在VSTO 增益集）。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="defining-a-range"></a>定義範圍  
 下列範例示範如何建立包含使用中文件中前七個字元 (包括非列印字元) 的新 <xref:Microsoft.Office.Interop.Word.Range> 物件。 它接著會選取範圍內的文字。  
  
#### <a name="to-define-a-range-in-a-document-level-customization"></a>定義文件層級自訂中的範圍  
  
1.  將開始和結束字元傳遞給 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Range%2A> 方法，以將範圍新增至文件。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
#### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>使用 VSTO 增益集定義範圍  
  
1.  將開始和結束字元傳遞給 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Range%2A> 方法，以將範圍新增至文件。 下列程式碼範例會將範圍新增至使用中文件。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="selecting-a-range-in-a-document-level-customization"></a>選取文件層級自訂中的範圍  
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Tools.Word.Document> 類別的 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性來選取整份文件。  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>使用 Select 方法將整份文件選取為範圍  
  
1.  使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>使用內容屬性將整份文件選取為範圍  
  
1.  使用 <xref:Microsoft.Office.Tools.Word.Document.Content%2A> 屬性定義包含整份文件的範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
 您也可以使用其他物件的方法和屬性來定義範圍。  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>選取使用中文件中的句子  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。 使用您想要選取之句子的索引。  
  
     [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
 另一種選取句子的方法是手動設定範圍的開始和結束值。  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>手動設定開始和結束值來選取句子  
  
1.  建立範圍變數。  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  若要查看是否有至少兩個句子，文件中的核取設定*啟動*和*結束*引數，以及該的範圍，然後選取範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="selecting-a-range-by-using-a-vsto-add-in"></a>使用 VSTO 增益集選取範圍  
 下列範例示範如何使用 <xref:Microsoft.Office.Interop.Word.Range> 物件的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法或使用 <xref:Microsoft.Office.Interop.Word.Document> 類別的 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性來選取整份文件。  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>使用 Select 方法將整份文件選取為範圍  
  
1.  使用包含整份文件之 <xref:Microsoft.Office.Interop.Word.Range> 的 <xref:Microsoft.Office.Interop.Word.Range.Select%2A> 方法。 下列程式碼範例會選取使用中文件的內容。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>使用內容屬性將整份文件選取為範圍  
  
1.  使用 <xref:Microsoft.Office.Interop.Word._Document.Content%2A> 屬性定義包含整份文件的範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
 您也可以使用其他物件的方法和屬性來定義範圍。  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>選取使用中文件中的句子  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Sentences> 集合設定範圍。 使用您想要選取之句子的索引。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
 另一種選取句子的方法是手動設定範圍的開始和結束值。  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>手動設定開始和結束值來選取句子  
  
1.  建立範圍變數。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  若要查看是否有至少兩個句子，文件中的核取設定*啟動*和*結束*引數，以及該的範圍，然後選取範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>另請參閱  
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [如何： 以程式設計方式擴充文件中的範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以程式設計方式擷取開頭和結尾字元範圍中](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何： 以程式設計方式擴充文件中的範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以程式設計方式在 Word 中重設範圍的文件](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何： 以程式設計方式摺疊範圍或選取的文件](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  