---
title: HOW TO：以程式設計方式隱藏 文件中的文字
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 1da471ff1911cdda4a62ef9c150236b3a225342f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110163"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>HOW TO：以程式設計方式隱藏 文件中的文字
  您可以針對文字的特定範圍設定 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 屬性，以隱藏文件中的文字。

 例如，您可以暫時隱藏內的文字<xref:Microsoft.Office.Tools.Word.Bookmark>（在文件層級自訂） 或<xref:Microsoft.Office.Interop.Word.Bookmark>（在 VSTO 增益集） 之前傳送至印表機的文件。

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
 此程式碼範例假設文件包含<xref:Microsoft.Office.Tools.Word.Bookmark>控制項 （在文件層級自訂） 或<xref:Microsoft.Office.Interop.Word.Bookmark>控制項 （在 VSTO 增益集），名為`bookmark1`。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)
- [如何：以程式設計方式定義，並在文件中選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式重設 Word 文件中的範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式更新書籤文字](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
