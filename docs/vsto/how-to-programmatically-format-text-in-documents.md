---
title: HOW TO：以程式設計方式在文件中的文字格式
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ba0c69768f8961fa6c23a599a385c46a93d7c47c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875390"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>HOW TO：以程式設計方式在文件中的文字格式
  您可以使用 <xref:Microsoft.Office.Interop.Word.Range> 物件格式化 Microsoft Office Word 文件中的文字。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 下列範例會選取文件中的第一個段落，並變更字型大小、字型名稱和對齊方式。 它接著會選取範圍，並顯示訊息方塊以在執行下個區塊的程式碼之前暫停。 下一個區段所呼叫的 Undo 方法<xref:Microsoft.Office.Tools.Word.Document>主項目 （適用於文件層級自訂） 或<xref:Microsoft.Office.Interop.Word.Document>類別 （適用於 VSTO 增益集） 三次。 它套用一般縮排樣式，並顯示訊息方塊以暫停程式碼。 接著，程式碼會呼叫 <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> 方法一次，並顯示訊息方塊。  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
### <a name="to-format-text-using-a-document-level-customization"></a>使用文件層級自訂格式化文字  
  
1.  下列範例可以用於文件層級自訂。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
### <a name="to-format-text-using-a-vsto-add-in"></a>使用 VSTO 增益集格式化文字  
  
1.  下列範例可以用於 VSTO 增益集。 本範例使用現用文件。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：以程式設計方式定義，並在文件中選取範圍](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何：以程式設計方式將文字插入 Word 文件](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何：以程式設計方式搜尋和取代文件中的文字](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
