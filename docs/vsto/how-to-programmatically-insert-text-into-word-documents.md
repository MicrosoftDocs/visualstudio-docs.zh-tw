---
title: 如何：以程式設計方式在 Word 檔中插入文字
description: 瞭解如何使用 Visual Studio，以程式設計方式將文字插入 Microsoft Word 檔。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9567ea197c9a181141aeb52db0cca56ad4776237
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525681"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>如何：以程式設計方式在 Word 檔中插入文字
  在 Microsoft Office Word 文件中插入文字的方式主要有三種：

- 在範圍中插入文字。

- 以新文字取代範圍中的文字。

- 使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Selection> 方法將文字插入游標或選取範圍。

> [!NOTE]
> 您也可以將文字插入內容控制項與書籤中。 如需詳細資訊，請參閱 [內容控制項](../vsto/content-controls.md) 和 [書簽控制項](../vsto/bookmark-control.md)。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>在範圍中插入文字
 使用 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> 物件的 <xref:Microsoft.Office.Interop.Word.Range> 屬性將文字插入文件。

### <a name="to-insert-text-in-a-range"></a>若要在範圍中插入文字

1. 在文件的開頭指定範圍，並插入文字 **New Text**。

     下列程式碼範例可用於文件層級自訂。

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. 選取 <xref:Microsoft.Office.Interop.Word.Range> 物件，這時物件已從一個字元擴展為所插入文字的長度。

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>取代範圍中的文字
 如果指定的範圍包含文字，則範圍內的所有文字都會以插入的文字取代。

### <a name="to-replace-text-in-a-range"></a>若要取代範圍中的文字

1. 建立一個包含文件中前 12 個字元的 <xref:Microsoft.Office.Interop.Word.Range> 物件。

     下列程式碼範例可用於文件層級自訂。

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. 以 **New Text** 字串取代這些字元。

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. 選取範圍。

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>使用 TypeText 插入文字
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 方法會在選取範圍插入文字。 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 的行為方式會因使用者電腦上設定的選項而異。 下列程序中的程式碼宣告了 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數，並且關閉 **Overtype** 選項 (如果是開啟的)。 如果啟用 **Overtype** 選項，則會覆寫游標後面的任何文字。

### <a name="to-insert-text-using-the-typetext-method"></a>若要使用 TypeText 方法插入文字

1. 宣告 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數。

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. 關閉 **Overtype** 選項 (如果是開啟的)。

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. 測試目前的選取範圍是否為插入點。

    如果是，程式碼就會使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>插入句子，然後使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> 方法插入段落標記。

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. **ElseIf** 區塊中的程式碼會進行測試，檢查選取範圍是否為一般的選取範圍。 如果是，則另一個 **If** 區塊就會測試 **ReplaceSelection** 選項是否已開啟。 如果該選項已開啟，程式碼就會使用選取範圍的 <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> 方法，將選取範圍摺疊至文字選取區塊起始處的插入點。 插入文字和段落標記。

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. 如果選取範圍不是插入點或選取文字的區塊，則 **Else** 區塊中的程式碼不會執行任何動作。

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   您也可以使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> 物件的方法 <xref:Microsoft.Office.Interop.Word.Selection> ，模擬鍵盤上 **倒退鍵** 的功能。 但是，如果要插入和處理文字， <xref:Microsoft.Office.Interop.Word.Range> 物件可以讓您有更多的控制能力。

   下列範例顯示完整程式碼。 若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行程式碼。

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式格式化檔中的文字](../vsto/how-to-programmatically-format-text-in-documents.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
