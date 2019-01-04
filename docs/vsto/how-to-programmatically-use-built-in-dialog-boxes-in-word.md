---
title: HOW TO：以程式設計方式使用 Word 中的內建對話方塊
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38e9fd10171bcc5be20f061217ff85b85ae3b52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829059"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>HOW TO：以程式設計方式使用 Word 中的內建對話方塊
  當使用 Microsoft Office Word 時，有當您需要顯示對話方塊，供使用者輸入的時間。 雖然您可以建立您自己，您也可以採取的方法使用的內建對話方塊在 Word 中，其公開於<xref:Microsoft.Office.Interop.Word.Dialogs>的集合<xref:Microsoft.Office.Interop.Word.Application>物件。 這可讓您存取超過 200 個內建的對話方塊，以列舉型別表示。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="display-dialog-boxes"></a>顯示對話方塊  
 若要顯示的對話方塊，請使用其中一個值<xref:Microsoft.Office.Interop.Word.WdWordDialog>列舉型別建立<xref:Microsoft.Office.Interop.Word.Dialog>物件，表示您想要顯示的對話方塊。 然後，呼叫<xref:Microsoft.Office.Interop.Word.Dialog.Show%2A>方法的<xref:Microsoft.Office.Interop.Word.Dialog>物件。  
  
 下列程式碼範例示範如何顯示**開啟舊檔** 對話方塊。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>存取對話方塊成員，都是透過晚期繫結  
 某些屬性和方法的對話方塊，在 Word 中都只能透過晚期繫結。 專案 Visual Basic 中的 where **Option Strict**已開啟，您必須使用反映來存取這些成員。 如需詳細資訊，請參閱 < [Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)。  
  
 下列程式碼範例示範如何使用**名稱**屬性**檔案開啟**對話方塊中，在 Visual Basic 專案的位置**Option Strict**關閉或在 Visual C#目標的專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下列程式碼範例示範如何使用反映來存取**名稱**屬性**檔案開啟**對話方塊中，在 Visual Basic 專案的位置**Option Strict**是上。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：以程式設計方式使用 Word 對話方塊，在隱藏模式中](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [Option strict 陳述式](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
