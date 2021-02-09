---
title: 如何：以程式設計方式在隱形模式中使用 Word 對話方塊
description: 瞭解如何使用 Visual Studio，以程式設計方式在隱形模式中使用 Microsoft Word 對話方塊。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0977e7241920ad23a6248bb2349ddaeb10a5e931
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931236"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>如何：以程式設計方式在隱形模式中使用 Word 對話方塊
  您可以叫用 Microsoft Office Word 中的內建對話方塊，而不將其顯示給使用者，藉此使用一個方法呼叫來執行複雜作業。 您可以使用物件的方法來完成這項作業， <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> <xref:Microsoft.Office.Interop.Word.Dialog> 而不需要呼叫 <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> 方法。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>範例
 下列程式碼範例示範如何使用隱形模式的 [版面 **設定** ] 對話方塊，設定多個沒有使用者輸入的版面設定屬性。 這些範例會使用 <xref:Microsoft.Office.Interop.Word.Dialog> 物件來設定自訂頁面大小。 版面設定的特定設定，例如上邊界、下邊界等，都可做為物件的晚期繫結屬性 <xref:Microsoft.Office.Interop.Word.Dialog> 。 這些屬性會在執行時間由 Word 動態建立。

 下列範例示範如何在 Visual Basic 專案中執行這項工作，其中 **Option Strict** 為 off，而 Visual c # 專案中的目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 在這些專案中，您可以在 Visual Basic 和 Visual c # 編譯器中使用晚期繫結功能。 若要使用此範例，請從 `ThisDocument` 專案的或 `ThisAddIn` 類別中執行它。

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 下列範例示範如何在 **Option Strict** 為 on 的 Visual Basic 專案中執行這項工作。 在這些專案中，您必須使用反映來存取晚期繫結屬性。 若要使用此範例，請從 `ThisDocument` 專案的或 `ThisAddIn` 類別中執行它。

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式使用 Word 中的內建對話方塊](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)
- [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
