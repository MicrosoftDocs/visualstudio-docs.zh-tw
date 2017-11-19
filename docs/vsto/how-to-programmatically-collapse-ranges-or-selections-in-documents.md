---
title: "如何： 以程式設計方式摺疊範圍或選取的文件 |Microsoft 文件"
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
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
ms.assetid: 0bd059dd-8606-42ae-a8a9-97f8f3bd5cc5
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 89430ca1b20df29bbd29af4ef41ceb7a9182564e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>如何：以程式設計方式摺疊文件的範圍或選取的範圍
  如果您正在使用 <xref:Microsoft.Office.Interop.Word.Range> 或 <xref:Microsoft.Office.Interop.Word.Selection> 物件，您可能會想要先將選取範圍變更為插入點再插入文字，以免覆寫現有的文字。 同時<xref:Microsoft.Office.Interop.Word.Range>和<xref:Microsoft.Office.Interop.Word.Selection>物件具有摺疊方法，其使用<xref:Microsoft.Office.Interop.Word.WdCollapseDirection>列舉值：  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 將選取範圍摺疊至選取範圍的開頭。 如果不指定列舉值，這就是預設值。  
  
-   <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 將選取範圍摺疊至選取範圍的結尾。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-collapse-a-range-and-insert-new-text"></a>摺疊範圍並插入新的文字  
  
1.  在文件中建立組成第一個段落的 <xref:Microsoft.Office.Interop.Word.Range> 物件。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]  
  
     下列程式碼範例可用於 VSTO 增益集。 這個程式碼會使用現用的文件。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> 列舉值摺疊範圍。  
  
     [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
     [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]  
  
3.  插入新的文字。  
  
     [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
     [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]  
  
4.  選取 <xref:Microsoft.Office.Interop.Word.Range>。  
  
     [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
     [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
 如果使用 <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> 列舉值，文字就會插入下列段落的開頭。  
  
 [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
 [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
 您可能希望將新句子插入在段落標記之前，但實際情況並非如此，因為原始範圍包含了段落標記。 如需詳細資訊，請參閱[How to： 以程式設計的方式排除段落標記時建立範圍](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)。  
  
## <a name="document-level-customization-example"></a>文件層級自訂範例  
  
#### <a name="to-collapse-a-range-in-a-document-level-customization"></a>摺疊文件層級自訂中的範圍  
  
1.  下列範例顯示文件層級自訂的完整方法。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>VSTO 增益集範例  
  
#### <a name="to-collapse-a-range-in-an-vsto-add-in"></a>摺疊 VSTO 增益集中的範圍  
  
1.  下列範例顯示 VSTO 增益集的完整方法。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式將文字插入 Word 文件](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何： 以程式設計方式擷取開頭和結尾字元範圍中](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [如何： 以程式設計方式建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何： 以程式設計方式擴充文件中的範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何：以程式設計方式在 Word 文件中重設範圍](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  