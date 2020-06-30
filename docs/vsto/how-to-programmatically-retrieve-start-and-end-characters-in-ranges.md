---
title: 以程式設計方式取得範圍中的開始 & 結束字元
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 485945f235a9161b6dc0584f7018c6f03c6024f5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537653"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>如何：以程式設計方式取出範圍中的開頭和結尾字元
  這個範例示範如何以字元位置形式，擷取範圍的開始和結尾位置。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>若要在文件層級自訂中擷取範圍的開始和結尾字元

1. 取得 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 物件之 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 和 <xref:Microsoft.Office.Interop.Word.Range> 屬性的值。 下列程式碼範例會取得文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>使用 VSTO 增益集來抓取範圍的開頭和結尾字元

1. 取得 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 物件之 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 和 <xref:Microsoft.Office.Interop.Word.Range> 屬性的值。 下列程式碼範例會取得使用中文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在檔中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式重設 Word 檔中的範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式折迭檔中的範圍或選取專案](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [如何：以程式設計方式計算檔中的字元](../vsto/how-to-programmatically-count-characters-in-documents.md)
