---
title: 以程式設計方式建立範圍時排除段落標記
description: 瞭解如何在 Microsoft Word 檔中建立範圍時，以程式設計的方式排除段落標記。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825793"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>如何：以程式設計方式在建立範圍時排除段落標記
  每當您根據段落建立 <xref:Microsoft.Office.Interop.Word.Range> 物件時，所有的非列印字元 (如段落標記) 都會包含在範圍中。 您可以將文字從來源段落插入目的段落。 如果您不想將目的段落分割成個別段落，則必須先移除來源段落的段落標記。 此外，因為段落格式化資訊儲存在段落標記內，所以在將範圍插入現有段落時，您可能不想包含該資訊。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 下列範例程序會宣告兩個字串變數，擷取現用文件的第一段和第二段內容，然後交換它們的內容。 下列範例示範使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 方法，從範圍移除段落標記，並在段落內插入文字。

## <a name="to-control-paragraph-structure-when-inserting-text"></a>若要在插入文字時控制段落結構

1. 針對第一和第二個段落建立兩個範圍變數，然後使用 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性擷取其內容。

     下列程式碼範例可用於文件層級自訂。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     下列程式碼範例可用於應用程式層級的 VSTO 增益集。 這個程式碼會使用現用的文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. 指派 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性，並將這兩個段落的文字互換。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. 依次選取每個範圍並暫停，以在訊息方塊中顯示結果。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. 使用 `firstRange` 方法調整 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> ，讓段落標記不再是 `firstRange`的一部分。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. 取代第一段中的其餘文字，指派新字串給該範圍的 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 屬性。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. 取代 `secondRange`中的文字，包括段落標記。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. 選取 `firstRange` 並暫停，以在訊息方塊中顯示結果，然後對 `secondRange`執行同樣的動作。

     因為已重新定義 `firstRange` 來排除段落標記，所以會保留段落的原始格式。 不過， `secondRange`中的段落標記上插入了句子，所以移除了個別段落。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     這兩個範圍的原始內容都儲存為字串，所以您可以將文件還原成原始狀態。

8. 重新調整 `firstRange` 以包含段落標記，方法是使用 <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> 單一字元位置的方法。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. 刪除 `secondRange`。 這會將段落三還原為原始的位置。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. 還原 `firstRange`中原始段落文字。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. 使用 <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Range> 方法，將原來第二段的內容插入 `firstRange`之後，然後選取 `firstRange`。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>檔層級自訂範例

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>若要在文件層級自訂中插入文字時控制段落結構

1. 下列範例顯示文件層級自訂的完整方法。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>若要在 VSTO 增益集中插入文字時控制段落結構

1. 下列範例顯示 VSTO 增益集的完整方法。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [如何：以程式設計方式折迭檔中的範圍或選取專案](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [如何：以程式設計方式在 Word 檔中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [如何：以程式設計方式在 Word 檔中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
