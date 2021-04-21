---
title: 如何：以程式設計方式在檔中擴充範圍
description: 瞭解如何以程式設計方式，在檔層級或應用層級上，以程式設計方式擴充 Microsoft Word 檔中的開始和結束點範圍。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a539bbbc4ad8d73477e660ef9903ac51dce712f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826521"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>如何：以程式設計方式在檔中擴充範圍
  在您定義 Microsoft Office Word 文件中的 <xref:Microsoft.Office.Interop.Word.Range> 物件之後，可以使用 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 和 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法來變更其起始點和結束點。 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>和 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法採用相同的兩個引數： *Unit* 和 *Count*。 *Count* 引數是要移動的單位數目，而 *Unit* 引數可以是下列其中一個 <xref:Microsoft.Office.Interop.Word.WdUnits> 值：

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  下列範例會定義一個七個字元的範圍， 然後將範圍的起始位置移到原始起始位置之後的七個字元處。 由於範圍的結束位置也是在起始位置之後的七個字元處，結果會使範圍包含零個字元。 程式碼接著會將結束位置移到目前結束位置之後的七個字元處。

## <a name="to-extend-a-range"></a>擴充範圍

1. 定義字元範圍。 如需詳細資訊，請參閱 [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)。

     下列程式碼範例可用於文件層級自訂。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. 使用 <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Range> 方法，移動範圍的起始位置。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. 使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Range> 方法，移動範圍的結束位置。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>檔層級自訂程式碼

### <a name="to-extend-a-range-in-a-document-level-customization"></a>擴充文件層級自訂中的範圍

1. 下列範例顯示文件層級自訂的完整程式碼。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>VSTO 增益集程式碼

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>擴充應用程式層級 VSTO 增益集中的範圍

1. 下列範例顯示 VSTO 增益集的完整程式碼。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在 Word 檔中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式折迭檔中的範圍或選取專案](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式取得範圍中的開始和結束字元](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [如何：以程式設計方式在建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
