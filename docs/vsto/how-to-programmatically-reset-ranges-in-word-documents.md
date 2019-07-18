---
title: HOW TO：以程式設計方式重設 Word 文件中的範圍
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622d807da832c4c07baf8b62c902c2b1d25cc14d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955691"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>HOW TO：以程式設計方式重設 Word 文件中的範圍
  使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 方法，可以調整 Microsoft Office Word 文件中現有範圍的大小。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>若要重設現有範圍

1. 以文件中前七個字元的開頭設定初始範圍。

     下列程式碼範例可用於文件層級自訂。

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. 使用 <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> 從第二個句子開始設定這個範圍，一直到第五個句子的結尾結束。

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>文件層級自訂範例

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>若要重設文件層級自訂中的現有範圍

1. 下列範例顯示文件層級自訂的完整範例。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>若要重設現有範圍中的 VSTO 增益集

1. 下列範例會顯示完整的範例，VSTO 增益集。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式擴充文件中的範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式定義，並在文件中選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式擷取範圍中的開頭和結尾字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [如何：以程式設計方式摺疊範圍或選取的文件](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
