---
title: 以程式設計方式將圖片和文字藝術新增至檔
description: 瞭解如何在設計階段或執行時間，將圖片和繪圖物件新增至您的檔。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding pictures
- Word documents, adding pictures
- Word documents, adding Word Art
- graphics, adding to Word documents
- WordArt, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0662c9324aaab8f5a368bc4db300ccff1a0ece33
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844045"
---
# <a name="how-to-programmatically-add-pictures-and-word-art-to-documents"></a>如何：以程式設計方式將圖片和文字藝術新增至檔
  您可以在設計階段或執行階段，將圖片和繪圖物件加入至您的文件。 文字藝術師可讓您將裝飾文字加入至 Microsoft Office Word 文件。 這些特殊文字效果是繪圖物件，您可自訂並將它們插入至文件。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="add-a-picture-at-design-time"></a>在設計階段加入圖片
 如果您正在開發文件層級自訂，可以在設計階段將圖片加入至文件。

### <a name="to-add-a-picture-to-a-word-document-at-design-time"></a>在設計階段將圖片加入至 Word 文件

1. 請將游標置於想要在文件中插入圖片的位置。

2. 按一下功能區的 [ **插入** ] 索引標籤。

3. 在 [ **圖例** ] 群組中，按一下 [ **圖片**]。

4. 在 [ **插入圖片** ] 對話方塊中，流覽至您要插入的圖片，然後按一下 [ **插入**]。

     圖片隨即加入文件中目前的游標位置。

## <a name="add-a-picture-at-run-time"></a>在執行時間加入圖片
 您可以將圖片插入文件中目前游標的位置。

### <a name="to-add-a-picture-at-the-cursor-location"></a>在游標位置加入圖片

1. 呼叫 <xref:Microsoft.Office.Interop.Word.InlineShapes> 集合的 <xref:Microsoft.Office.Interop.Word.InlineShapes.AddPicture%2A> 方法，並傳入檔案的名稱。

     [!code-vb[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#108)]
     [!code-csharp[Trin_VstcoreWordAutomation#108](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#108)]

## <a name="add-wordart-at-design-time"></a>在設計階段加入藝術
 如果您正在開發文件層級自訂，可以在設計階段將文字藝術師加入至文件。

### <a name="to-add-wordart-to-a-word-document-at-design-time"></a>在設計階段將文字藝術師加入至 Word 文件

1. 請將游標置於想要在文件中插入文字藝術師的位置。

2. 按一下功能區的 [ **插入** ] 索引標籤。

3. 在 [ **文字** ] 群組中，按一下 [ **藝術字**]，然後選取 [藝術體] 樣式。

4. 將您想要在檔中顯示的文字加入至 [ **編輯藝術文字** ] 對話方塊中，然後按一下 **[確定]**。

     加入至文件的文字即會套用選取的文字藝術師樣式。

## <a name="add-wordart-at-run-time"></a>在執行時間加入藝術
 您可以將文字藝術師插入至文件中目前游標的位置。 文件層級自訂與 VSTO 增益集的程序不同。

### <a name="to-add-wordart-at-the-cursor-location-in-a-document-level-customization"></a>在文件層級自訂的游標位置加入文字藝術師

1. 取得目前游標位置的左端和頂端位置。

     [!code-vb[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomation#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#109)]

2. 請呼叫文件中 <xref:Microsoft.Office.Interop.Word.Shapes> 物件的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。

     [!code-vb[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomation#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#110)]

### <a name="to-add-wordart-at-the-cursor-location-in-a-vsto-add-in"></a>在 VSTO 增益集的游標位置加入文字藝術師

1. 取得目前游標位置的左端和頂端位置。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#109)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#109](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#109)]

2. 請呼叫使用中文件 (或您所指定的不同文件) 之 <xref:Microsoft.Office.Interop.Word.Shapes> 物件的 <xref:Microsoft.Office.Interop.Word.Shapes.AddTextEffect%2A> 方法。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#110)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#110](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#110)]

## <a name="compile-the-code"></a>編譯程式碼

- 磁片磁碟機 C 上必須存在名為 *SamplePicture.jpg* 的圖片。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式開啟現有檔](../vsto/how-to-programmatically-open-existing-documents.md)
- [如何：以程式設計方式在 Word 檔中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [如何：以程式設計方式在搜尋後還原選取專案](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [如何：以程式設計方式儲存檔](../vsto/how-to-programmatically-save-documents.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
