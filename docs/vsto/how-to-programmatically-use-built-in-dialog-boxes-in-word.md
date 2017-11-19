---
title: "如何： 以程式設計方式使用 Word 中的內建對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd7d81837699aedd1c6c61d0cb0d9e2e9a64db4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>如何：以程式設計方式使用 Word 中的內建對話方塊
  與 Microsoft Office Word 時，有您需要顯示使用者輸入的對話方塊。 雖然您可以建立您自己，可能也想要使用的內建對話方塊在 Word 中，會公開在方法<xref:Microsoft.Office.Interop.Word.Dialogs>集合<xref:Microsoft.Office.Interop.Word.Application>物件。 這可讓您存取超過 200 的內建對話方塊方塊中，會以列舉型別表示。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>顯示對話方塊  
 若要顯示一個對話方塊，請使用其中一個值的<xref:Microsoft.Office.Interop.Word.WdWordDialog>列舉型別建立<xref:Microsoft.Office.Interop.Word.Dialog>物件，表示您想要顯示的對話方塊。 然後，呼叫<xref:Microsoft.Office.Interop.Word.Dialog.Show%2A>方法<xref:Microsoft.Office.Interop.Word.Dialog>物件。  
  
 下列程式碼範例示範如何顯示**開啟舊檔** 對話方塊。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>存取可透過晚期繫結對話方塊成員  
 某些屬性和方法，在 Word 中的對話方塊可用只能透過晚期繫結。 專案 Visual Basic 中的 where **Option Strict**已開啟，您必須使用反映來存取這些成員。 如需詳細資訊，請參閱 [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md)。  
  
 下列程式碼範例示範如何使用**名稱**屬性**開啟舊檔**對話方塊中，在 Visual Basic 專案 where **Option Strict**關閉或 Visual C# 中目標的專案[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]或[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 下列程式碼範例示範如何使用反映來存取**名稱**屬性**開啟舊檔**對話方塊中，在 Visual Basic 專案 where **Option Strict**是上。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式使用 Word 對話方塊在隱藏模式中](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict 陳述式](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  