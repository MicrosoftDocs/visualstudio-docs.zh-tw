---
title: 如何：以程式設計方式使用 Word 中的內建對話方塊
description: 瞭解如何使用 Visual Studio，以程式設計方式使用 Microsoft Word 內建的對話方塊。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 18a6176c6472f1587e00364f0e0bd300611eabf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897517"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>如何：以程式設計方式使用 Word 中的內建對話方塊
  使用 Microsoft Office Word 時，有時您需要顯示使用者輸入的對話方塊。 雖然您可以建立自己的，但您也可能想要使用 Word 中的內建對話方塊，這是在物件的集合中公開的 <xref:Microsoft.Office.Interop.Word.Dialogs> <xref:Microsoft.Office.Interop.Word.Application> 。 這可讓您存取200以上的內建對話方塊（以列舉表示）。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>顯示對話方塊
 若要顯示對話方塊，請使用列舉的其中一個值 <xref:Microsoft.Office.Interop.Word.WdWordDialog> 來建立 <xref:Microsoft.Office.Interop.Word.Dialog> 代表您要顯示之對話方塊的物件。 然後，呼叫 <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> 物件的方法 <xref:Microsoft.Office.Interop.Word.Dialog> 。

 下列程式碼範例示範如何顯示 [ **開啟** 檔案] 對話方塊。 若要使用此範例，請從 `ThisDocument` 專案的或 `ThisAddIn` 類別中執行它。

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>可透過晚期繫結取得的存取對話方塊成員
 Word 中對話方塊的部分屬性和方法只能透過晚期繫結來使用。 在 **Option Strict** 為 on Visual Basic 專案中，您必須使用反映來存取這些成員。 如需詳細資訊，請參閱 [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。

 下列程式碼範例示範如何使用 [**開啟**] 對話方塊的 [**名稱**] 屬性，在 [ **Option Strict** ] 為 off 的 Visual Basic 專案中，或在以或為目標的 Visual c # 專案中使用 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 。 若要使用此範例，請從 `ThisDocument` 專案的或 `ThisAddIn` 類別中執行它。

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 下列程式碼範例示範如何在 **Option Strict** 為 on 的 Visual Basic 專案中，使用反映來存取 [**開啟** 檔案] 對話方塊的 [**名稱**] 屬性。 若要使用此範例，請從 `ThisDocument` 專案的或 `ThisAddIn` 類別中執行它。

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式在隱形模式中使用 Word 對話方塊](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict 語句](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
