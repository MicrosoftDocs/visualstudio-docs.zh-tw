---
title: 如何：以程式設計方式在檔中隱藏文字
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dae19d196f830e5187fa395473c0a5482cb1d03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543308"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>如何：以程式設計方式在檔中隱藏文字
  您可以針對文字的特定範圍設定 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 屬性，以隱藏文件中的文字。

 例如，您可以在將 <xref:Microsoft.Office.Tools.Word.Bookmark> 檔傳送至印表機之前，暫時隱藏（在檔層級自訂中）或 <xref:Microsoft.Office.Interop.Word.Bookmark> （在 VSTO 增益集中）中的文字。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>在列印文件時隱藏書籤控制項中的文字

1. 建立隱藏指定範圍內所有文字的程序。

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. 建立取消隱藏指定範圍內所有文字的程序。

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. 將書籤範圍傳遞給 `HideText` 方法、列印文件，然後將相同範圍傳遞給 `UnhideText` 方法。

     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>編譯程式碼
 這個程式碼範例假設檔包含 <xref:Microsoft.Office.Tools.Word.Bookmark> 名為的控制項（在檔層級自訂中）或 <xref:Microsoft.Office.Interop.Word.Bookmark> 控制項（在 VSTO 增益集中） `bookmark1` 。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式列印檔案](../vsto/how-to-programmatically-print-documents.md)
- [如何：以程式設計方式在檔中定義及選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式重設 Word 檔中的範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式更新書簽文字](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
