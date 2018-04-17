---
title: 如何： 以程式設計方式隱藏文件中的文字 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8e2ea2f5f8af3876fe64d90d5f2d77874ebb252
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>如何：以程式設計方式在文件中隱藏文字
  您可以針對文字的特定範圍設定 <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> 的 <xref:Microsoft.Office.Interop.Word.Range.Font%2A> 屬性，以隱藏文件中的文字。  
  
 例如，您可以暫時隱藏 <xref:Microsoft.Office.Tools.Word.Bookmark> (文件層級自訂) 或 <xref:Microsoft.Office.Interop.Word.Bookmark> (VSTO 增益集) 內的文字，再將文件傳送至印表機。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>在列印文件時隱藏書籤控制項中的文字  
  
1.  建立隱藏指定範圍內所有文字的程序。  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  建立取消隱藏指定範圍內所有文字的程序。  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  將書籤範圍傳遞給 `HideText` 方法、列印文件，然後將相同範圍傳遞給 `UnhideText` 方法。  
  
     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例假設文件包含名為 <xref:Microsoft.Office.Tools.Word.Bookmark> 的 <xref:Microsoft.Office.Interop.Word.Bookmark> 控制項 (文件層級自訂) 或 `bookmark1`控制項 (VSTO 增益集)。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式列印文件](../vsto/how-to-programmatically-print-documents.md)   
 [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何： 以程式設計方式在 Word 中重設範圍的文件](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何： 以程式設計方式更新書籤文字](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  