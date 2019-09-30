---
title: HOW TO：以程式設計方式在隱形模式中使用 Word 對話方塊
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255854"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>作法：以程式設計方式在隱形模式中使用 Word 對話方塊
  藉由叫用 Microsoft Office Word 中的內建對話方塊，而不向使用者顯示，您可以使用一個方法呼叫來執行複雜的作業。 您可以使用<xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> <xref:Microsoft.Office.Interop.Word.Dialog>物件的方法來執行這項操作，而不<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>需要呼叫方法。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>範例
 下列程式碼範例示範如何使用隱形模式的 [版面**設定**] 對話方塊，設定多個不含使用者輸入的版面設定屬性。 這些範例會使用<xref:Microsoft.Office.Interop.Word.Dialog>物件來設定自訂頁面大小。 頁面設定的特定設定（例如上邊界、下邊界等等）可作為<xref:Microsoft.Office.Interop.Word.Dialog>物件的晚期繫結屬性。 這些屬性是由 Word 在執行時間動態建立的。

 下列範例示範如何在 Visual Basic 專案中執行這項工作，其中**Option Strict**是 off，而C#在以為目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]的 Visual 專案中。 在這些專案中，您可以使用 Visual Basic 和 Visual C#編譯器中的晚期繫結功能。 若要使用此範例，請從專案`ThisDocument`中`ThisAddIn`的或類別執行它。

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 下列範例示範如何在**Option Strict**為 on 的 Visual Basic 專案中執行這項工作。 在這些專案中，您必須使用反映來存取晚期繫結屬性。 若要使用此範例，請從專案`ThisDocument`中`ThisAddIn`的或類別執行它。

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式使用 Word 中的內建對話方塊](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word 物件模型總覽](../vsto/word-object-model-overview.md)
- [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)
- [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
