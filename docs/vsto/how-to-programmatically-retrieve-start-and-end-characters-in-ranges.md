---
title: "如何： 以程式設計方式擷取開頭和結尾字元範圍中的 |Microsoft 文件"
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
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 51f88435a5dff346e3de793b408f67e2837478e8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>如何：以程式設計方式擷取範圍中的開頭和結尾字元
  這個範例示範如何以字元位置形式，擷取範圍的開始和結尾位置。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>若要在文件層級自訂中擷取範圍的開始和結尾字元  
  
1.  取得 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 物件之 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 和 <xref:Microsoft.Office.Interop.Word.Range> 屬性的值。 下列程式碼範例會取得文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisDocument` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>若要使用 VSTO 增益集擷取範圍的開頭和結尾字元  
  
1.  取得 <xref:Microsoft.Office.Interop.Word.Range.Start%2A> 物件之 <xref:Microsoft.Office.Interop.Word.Range.End%2A> 和 <xref:Microsoft.Office.Interop.Word.Range> 屬性的值。 下列程式碼範例會取得使用中文件中第二句的開始和結尾位置。 若要使用此程式碼範例，請從專案的 `ThisAddIn` 類別中執行它。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式定義及選取範圍中的文件](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [如何： 以程式設計方式擴充文件中的範圍](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [如何： 以程式設計方式在 Word 中重設範圍的文件](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [如何： 以程式設計方式摺疊範圍或選取的文件](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [如何： 以程式設計方式建立範圍時排除段落標記](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [如何：以程式設計方式計算文件中的字元數](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  