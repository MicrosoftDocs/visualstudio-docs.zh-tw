---
title: "如何： 以程式設計方式建立 Word 表格 |Microsoft 文件"
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
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c903ed815e35c3d4f6821d70910ef56611889f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-word-tables"></a>如何：以程式設計方式建立 Word 表格
  <xref:Microsoft.Office.Interop.Word.Tables> 集合是 <xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Tools.Word.Document>、<xref:Microsoft.Office.Interop.Word.Selection> 及 <xref:Microsoft.Office.Interop.Word.Range> 類別的成員，表示您可以在其中任何一個內容中建立資料表。 您使用 <xref:Microsoft.Office.Interop.Word.Tables> 集合的 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法，加入指定範圍的表格。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>在文件層級自訂中建立表格  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>在文件中加入簡單的表格  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法，在文件開頭加入包含三列四行的表格。  
  
     若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 當您建立表格時，表格會自動加入 <xref:Microsoft.Office.Tools.Word.Document> 主項目的 <xref:Microsoft.Office.Interop.Word.Tables> 集合。 您可以利用下列程式碼中所示的 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 屬性，依表格的項目編號來參考表格。  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>依項目編號參考表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 屬性，並提供您要參考之表格的項目編號。  
  
     若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 每個 <xref:Microsoft.Office.Interop.Word.Table> 物件都有 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 屬性可以讓您設定的格式化屬性。  
  
#### <a name="to-apply-a-style-to-a-table"></a>將樣式套用到表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 屬性，將任一種 Word 內建樣式套用到表格。  
  
     若要使用下列程式碼範例，請從專案的 `ThisDocument` 類別中執行此範例。  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>在 VSTO 增益集中建立表格  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>在文件中加入簡單的表格  
  
-   使用 <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> 方法，在文件開頭加入包含三列四行的表格。  
  
     下列程式碼範例會在使用中文件內加入表格。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 當您建立表格時，表格會自動加入 <xref:Microsoft.Office.Interop.Word.Document> 的 <xref:Microsoft.Office.Interop.Word.Tables> 集合中。 您可以利用下列程式碼中所示的 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 屬性，依表格的項目編號來參考表格。  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>依項目編號參考表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> 屬性，並提供您要參考之表格的項目編號。  
  
     下列程式碼範例會使用使用中的文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 每個 <xref:Microsoft.Office.Interop.Word.Table> 物件都有 <xref:Microsoft.Office.Interop.Word.Table.Range%2A> 屬性可以讓您設定的格式化屬性。  
  
#### <a name="to-apply-a-style-to-a-table"></a>將樣式套用到表格  
  
1.  使用 <xref:Microsoft.Office.Interop.Word.Table.Style%2A> 屬性，將任一種 Word 內建樣式套用到表格。  
  
     下列程式碼範例會使用使用中的文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式加入文字和格式在 Word 表格的儲存格](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [如何： 以程式設計方式將資料列和資料行加入至 Word 表格](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何： 以程式設計方式填入 Word 表格的文件屬性](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  