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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827353"
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

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. 選取 <xref:Microsoft.Office.Interop.Word.Range> 物件，這時物件已從一個字元擴展為所插入文字的長度。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>取代範圍中的文字
 如果指定的範圍包含文字，則範圍內的所有文字都會以插入的文字取代。

### <a name="to-replace-text-in-a-range"></a>若要取代範圍中的文字

1. 建立一個包含文件中前 12 個字元的 <xref:Microsoft.Office.Interop.Word.Range> 物件。

     下列程式碼範例可用於文件層級自訂。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. 以 **New Text** 字串取代這些字元。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. 選取範圍。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>使用 TypeText 插入文字
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 方法會在選取範圍插入文字。 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> 的行為方式會因使用者電腦上設定的選項而異。 下列程序中的程式碼宣告了 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數，並且關閉 **Overtype** 選項 (如果是開啟的)。 如果啟用 **Overtype** 選項，則會覆寫游標後面的任何文字。

### <a name="to-insert-text-using-the-typetext-method"></a>若要使用 TypeText 方法插入文字

1. 宣告 <xref:Microsoft.Office.Interop.Word.Selection> 物件變數。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. 關閉 **Overtype** 選項 (如果是開啟的)。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. 測試目前的選取範圍是否為插入點。

    如果是，程式碼就會使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>插入句子，然後使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> 方法插入段落標記。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. **ElseIf** 區塊中的程式碼會進行測試，檢查選取範圍是否為一般的選取範圍。 如果是，則另一個 **If** 區塊就會測試 **ReplaceSelection** 選項是否已開啟。 如果該選項已開啟，程式碼就會使用選取範圍的 <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> 方法，將選取範圍摺疊至文字選取區塊起始處的插入點。 插入文字和段落標記。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. 如果選取範圍不是插入點或選取文字的區塊，則 **Else** 區塊中的程式碼不會執行任何動作。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   您也可以使用 <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> 物件的方法 <xref:Microsoft.Office.Interop.Word.Selection> ，模擬鍵盤上 **倒退鍵** 的功能。 但是，如果要插入和處理文字， <xref:Microsoft.Office.Interop.Word.Range> 物件可以讓您有更多的控制能力。

   下列範例顯示完整程式碼。 若要使用這個範例，請從專案中的 `ThisDocument` 或 `ThisAddIn` 類別中執行程式碼。

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式格式化檔中的文字](../vsto/how-to-programmatically-format-text-in-documents.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在檔中擴充範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
