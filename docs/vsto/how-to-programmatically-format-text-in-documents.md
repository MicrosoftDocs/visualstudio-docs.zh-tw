---
title: 如何：以程式設計方式格式化檔中的文字
description: 瞭解如何使用 Range 物件以程式設計方式格式化 Microsoft Word 檔中的文字。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 931991529b160fedfe65a92e8243183792abf518
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525731"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>如何：以程式設計方式格式化檔中的文字
  您可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件格式化 Microsoft Office Word 文件中的文字。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 下列範例會選取文件中的第一個段落，並變更字型大小、字型名稱和對齊方式。 它接著會選取範圍，並顯示訊息方塊以在執行下個區塊的程式碼之前暫停。 下一節會 <xref:Microsoft.Office.Tools.Word.Document> 針對檔層級自訂) 呼叫主專案 (的復原方法，或將 <xref:Microsoft.Office.Interop.Word.Document> VSTO 增益集的類別 () 三次。 它套用一般縮排樣式，並顯示訊息方塊以暫停程式碼。 接著，程式碼會呼叫 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 方法一次，並顯示訊息方塊。

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
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在 Word 檔中插入文字](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [如何：以程式設計方式搜尋和取代檔中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
