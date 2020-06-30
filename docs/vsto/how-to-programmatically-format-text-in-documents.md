---
title: 如何：以程式設計方式格式化檔中的文字
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76af290b0e32126689dbe7b60f27889d9742ea7f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519843"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>如何：以程式設計方式格式化檔中的文字
  您可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件格式化 Microsoft Office Word 文件中的文字。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 下列範例會選取文件中的第一個段落，並變更字型大小、字型名稱和對齊方式。 它接著會選取範圍，並顯示訊息方塊以在執行下個區塊的程式碼之前暫停。 下一節會呼叫 <xref:Microsoft.Office.Tools.Word.Document> 主專案（適用于檔層級自訂）或 <xref:Microsoft.Office.Interop.Word.Document> 類別（適用于 VSTO 增益集）的復原方法三次。 它套用一般縮排樣式，並顯示訊息方塊以暫停程式碼。 接著，程式碼會呼叫 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 方法一次，並顯示訊息方塊。

## <a name="document-level-customization-example"></a>檔層級自訂範例

### <a name="to-format-text-using-a-document-level-customization"></a>使用文件層級自訂格式化文字

1. 下列範例可以用於文件層級自訂。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>VSTO 增益集範例

### <a name="to-format-text-using-a-vsto-add-in"></a>使用 VSTO 增益集格式化文字

1. 下列範例可以用於 VSTO 增益集。 本範例使用現用文件。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在檔中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式將文字插入 Word 檔](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [如何：以程式設計方式在檔中搜尋和取代文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
