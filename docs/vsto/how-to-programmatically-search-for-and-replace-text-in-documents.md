---
title: "如何： 以程式設計方式搜尋和取代文件中的文字 |Microsoft 文件"
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
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 658da08ee7d61651b02d7d42158637dad7ab16c4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-and-replace-text--in-documents"></a>如何：以程式設計方式在文件中搜尋和取代文字
  <xref:Microsoft.Office.Interop.Word.Find> 物件是 <xref:Microsoft.Office.Interop.Word.Selection> 和 <xref:Microsoft.Office.Interop.Word.Range> 物件共有的成員，您可以使用這個成員在 Microsoft Office Word 文件中搜尋文字。 取代命令是尋找命令的擴充功能。  
  
 使用 <xref:Microsoft.Office.Interop.Word.Find> 物件在 Microsoft Office Word 文件中逐一搜尋特定的文字、格式或樣式，並使用 <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> 屬性取代任何找到的項目。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-a-selection-object"></a>使用 Selection 物件  
 使用 <xref:Microsoft.Office.Interop.Word.Selection> 物件尋找文字時，所指定的任何搜尋準則都只會套用至目前選取的文字。 如果 <xref:Microsoft.Office.Interop.Word.Selection> 是插入點，則會搜尋該文件。 找到符合搜尋準則的項目時，便會自動選取該項目。  
  
 請務必注意，<xref:Microsoft.Office.Interop.Word.Find> 準則是累加式的，這意味著準則會加入先前的搜尋準則。 進行搜尋前，請使用 <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> 方法清除之前搜尋的格式設定。  
  
#### <a name="to-find-text-using-a-selection-object"></a>使用 Selection 物件尋找文字  
  
1.  將搜尋字串指派至變數。  
  
     [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
     [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2.  清除之前搜尋的格式設定。  
  
     [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
     [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3.  執行搜尋並顯示含有結果的訊息方塊。  
  
     [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
     [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
 下列範例示範完整的方法：  
  
 [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
 [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="using-a-range-object"></a>使用 Range 物件  
 使用 <xref:Microsoft.Office.Interop.Word.Range> 物件可讓您搜尋文字，而不必在使用者介面中顯示任何資訊。 <xref:Microsoft.Office.Interop.Word.Find>物件會傳回**True**如果找到符合的搜尋條件的文字和**False**如果不存在。 如果找到文字，該方法還會重新定義 <xref:Microsoft.Office.Interop.Word.Range> 物件以符合搜尋準則。  
  
#### <a name="to-find-text-using-a-range-object"></a>使用 Range 物件尋找文字  
  
1.  定義一個由文件第二段組成的 <xref:Microsoft.Office.Interop.Word.Range> 物件。  
  
     下列程式碼範例可用於文件層級自訂。  
  
     [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2.  使用<xref:Microsoft.Office.Interop.Word.Range.Find%2A>屬性<xref:Microsoft.Office.Interop.Word.Range>物件，先清除任何現有的格式選項，然後搜尋字串**找到我**。  
  
     [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
     [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3.  在訊息方塊中顯示搜尋結果，並選取 <xref:Microsoft.Office.Interop.Word.Range> 以讓它顯示。  
  
     [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
     [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
     如果搜尋失敗，就會選取第二段；如果成功，就會顯示搜尋準則。  
  
 下列範例顯示文件層級自訂的完整程式碼。 若要使用這個範例，請從專案中的 `ThisDocument` 類別執行程式碼。  
  
 [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
 下列範例顯示 VSTO 增益集的完整程式碼。 若要使用這個範例，請從專案中的 `ThisAddIn` 類別執行程式碼。  
  
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="searching-for-and-replacing-text-in-documents"></a>搜尋和取代文件中的文字  
 下列程式碼搜尋目前的選取範圍，並會取代所有相符字串**找到我**字串**發現**。  
  
#### <a name="to-search-for-and-replace-text-in-documents"></a>搜尋和取代文件中的文字  
  
1.  請將下列範例程式碼加入專案的 `ThisDocument` 或 `ThisAddIn` 類別。  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> 類別具有 <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> 方法，而 <xref:Microsoft.Office.Interop.Word.Replacement> 類別也有自己的 <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> 方法。 當您執行尋找和取代作業時，您必須使用這兩個物件的 ClearFormatting 方法。 如果您只在 <xref:Microsoft.Office.Interop.Word.Find> 物件上使用它，則可能會在取代文字中得到非預期的結果。  
  
2.  使用 <xref:Microsoft.Office.Interop.Word.Find> 物件的 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 方法取代每一個找到的項目。 若要指定要取代的項目，請使用*取代*參數。 這個參數可以是下列其中一個 <xref:Microsoft.Office.Interop.Word.WdReplace> 值：  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> 會取代所有找到的項目。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> 不會取代任何找到的項目。  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> 會取代第一個找到的項目。  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式在 Word 中設定搜尋選項](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [如何： 以程式設計方式重複使用文件中找到的項目](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何： 以程式設計方式搜尋後還原選取](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  