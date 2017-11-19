---
title: "如何： 以程式設計方式使用 Word 對話方塊在隱藏模式中的 |Microsoft 文件"
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
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: daf5cfb79c16a26b871e2c4d07ec304c17cb6a33
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>如何：以程式設計方式在隱藏模式中使用 Word 對話方塊
  您可以藉由叫用 Microsoft Office Word 中的內建對話方塊，而不會向使用者顯示這些執行複雜的作業，包含一個方法呼叫。 您可以使用<xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A>方法<xref:Microsoft.Office.Interop.Word.Dialog>物件而不需呼叫<xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>方法。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="examples"></a>範例  
 下列程式碼範例示範如何使用**版面** 對話方塊中設定多個頁面上設定屬性，不需要使用者輸入的隱藏模式。 這些範例使用<xref:Microsoft.Office.Interop.Word.Dialog>物件來設定自訂頁面大小。 為晚期繫結的屬性可用之特定設定的 版面設定，例如邊界、 下邊界和等等，<xref:Microsoft.Office.Interop.Word.Dialog>物件。 Word 在執行階段以動態方式建立這些屬性。  
  
 下列範例示範如何在 Visual Basic 專案中執行此工作其中**Option Strict**是 off 和 Visual C# 專案中目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 在這些專案中，您可以在 Visual Basic 和 Visual C# 編譯器使用晚期繫結功能。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]  
  
 下列範例示範如何在 Visual Basic 專案中執行此工作其中**Option Strict**上。 在這些專案中，您必須使用反映來存取晚期繫結屬性。 若要使用此範例中，執行從`ThisDocument`或`ThisAddIn`專案中的類別。  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式使用 Word 中的內建對話方塊](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Word 物件模型概觀](../vsto/word-object-model-overview.md)   
 [在 Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)   
 [反映 (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [反映 (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  