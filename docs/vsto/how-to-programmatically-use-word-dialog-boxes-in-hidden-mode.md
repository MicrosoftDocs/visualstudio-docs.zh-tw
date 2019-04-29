---
title: HOW TO：以程式設計方式使用 Word 對話方塊，在隱藏模式中
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
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961601"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>HOW TO：以程式設計方式使用 Word 對話方塊，在隱藏模式中
  您可以藉由叫用 Microsoft Office Word 中的內建對話方塊，而不向使用者顯示這些執行複雜的作業，其中一種方法的呼叫取代。 您可以使用<xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A>方法<xref:Microsoft.Office.Interop.Word.Dialog>物件，而不需呼叫<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>方法。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>範例
 下列程式碼範例示範如何使用**版面** 對話方塊中，將多個頁面版面設定屬性設定不需要使用者輸入的隱藏模式。 範例會使用<xref:Microsoft.Office.Interop.Word.Dialog>物件來設定自訂的頁面大小。 上邊界、 下邊界，並依此類推，例如版面設定的特定設定是晚期繫結屬性的<xref:Microsoft.Office.Interop.Word.Dialog>物件。 以單字來在執行階段以動態方式建立這些屬性。

 下列範例示範如何在 Visual Basic 專案中執行這項工作中何處**Option Strict**是關閉，而在 Visual C# 專案的目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 在這些專案中，您可以在 Visual Basic 和 Visual C# 編譯器使用晚期繫結功能。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 下列範例示範如何在 Visual Basic 專案中執行這項工作中何處**Option Strict**上。 在這些專案中，您必須使用反映來存取晚期繫結屬性。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式使用 Word 中的內建對話方塊](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Word 物件模型概觀](../vsto/word-object-model-overview.md)
- [在 Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)
- [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
