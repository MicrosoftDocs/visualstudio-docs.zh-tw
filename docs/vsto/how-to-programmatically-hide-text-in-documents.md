---
title: 如何：以程式設計方式隱藏檔中的文字
description: 瞭解如何藉由針對特定文字範圍設定字型的隱藏屬性，隱藏 Microsoft Word 檔中的文字。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a375e8b844f82b5d310841d7b4cdc092b18ff6c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525695"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>如何：以程式設計方式隱藏檔中的文字
  您可以針對文字的特定範圍設定 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 屬性，以隱藏文件中的文字。

 例如，您可以在 <xref:Microsoft.Office.Tools.Word.Bookmark> 檔層級自訂) 或 VSTO 增益集) 中的 (，暫時隱藏 (內的文字， <xref:Microsoft.Office.Interop.Word.Bookmark> 然後再將檔傳送至印表機。

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
 這個程式碼範例假設檔在 <xref:Microsoft.Office.Tools.Word.Bookmark> 檔層級自訂中包含控制項 () 或 <xref:Microsoft.Office.Interop.Word.Bookmark> 在名為的 VSTO 增益集) 中控制 (`bookmark1` 。

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式列印檔案](../vsto/how-to-programmatically-print-documents.md)
- [如何：以程式設計方式定義和選取檔中的範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [如何：以程式設計方式在 Word 檔中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [如何：以程式設計方式更新書簽文字](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
