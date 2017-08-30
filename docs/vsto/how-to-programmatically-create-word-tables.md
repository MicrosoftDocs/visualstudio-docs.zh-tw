---
title: 'How to: Programmatically Create Word Tables | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 206109fae04dfdce7ac94d15194ef66de720b076
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-create-word-tables"></a>How to: Programmatically Create Word Tables
  The <xref:Microsoft.Office.Interop.Word.Tables> collection is a member of the <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, and <xref:Microsoft.Office.Interop.Word.Range> classes, which means that you can create a table in any of those contexts. You use the <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> method of the <xref:Microsoft.Office.Interop.Word.Tables> collection to add a table at the specified range.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="creating-tables-in-document-level-customizations"></a>Creating Tables in Document-Level Customizations  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>To add a simple table to a document  
  
-   Use the <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> method to add a table consisting of three rows and four columns at the beginning of the document.  
  
     To use the following code example, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]  [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
 When you create a table, it is automatically added to the <xref:Microsoft.Office.Interop.Word.Tables> collection of the <xref:Microsoft.Office.Tools.Word.Document> host item. You can then refer to the table by its item number by using the <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> property, as shown in the following code.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>To refer to a table by item number  
  
1.  Use the <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> property and supply the item number of the table that you want to refer to.  
  
     To use the following code example, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]  [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
 Each <xref:Microsoft.Office.Interop.Word.Table> object also has a <xref:Microsoft.Office.Interop.Word.Table.Range%2A> property that enables you to set formatting attributes.  
  
#### <a name="to-apply-a-style-to-a-table"></a>To apply a style to a table  
  
1.  Use the <xref:Microsoft.Office.Interop.Word.Table.Style%2A> property to apply one of the Word built-in styles to a table.  
  
     To use the following code example, run it from the `ThisDocument` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]  [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="creating-tables-in-vsto-add-ins"></a>Creating Tables in VSTO Add-ins  
  
#### <a name="to-add-a-simple-table-to-a-document"></a>To add a simple table to a document  
  
-   Use the <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> method to add a table consisting of three rows and four columns at the beginning of the document.  
  
     The following code example adds a table to the active document. To use this example, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
 When you create a table, it is automatically added to the <xref:Microsoft.Office.Interop.Word.Tables> collection of the <xref:Microsoft.Office.Interop.Word.Document>. You can then refer to the table by its item number by using the <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> property, as shown in the following code.  
  
#### <a name="to-refer-to-a-table-by-item-number"></a>To refer to a table by item number  
  
1.  Use the <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> property and supply the item number of the table that you want to refer to.  
  
     The following code example uses the active document. To use this example, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
 Each <xref:Microsoft.Office.Interop.Word.Table> object also has a <xref:Microsoft.Office.Interop.Word.Table.Range%2A> property that enables you to set formatting attributes.  
  
#### <a name="to-apply-a-style-to-a-table"></a>To apply a style to a table  
  
1.  Use the <xref:Microsoft.Office.Interop.Word.Table.Style%2A> property to apply one of the Word built-in styles to a table.  
  
     The following code example uses the active document. To use this example, run it from the `ThisAddIn` class in your project.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]  [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>See Also  
 [How to: Programmatically Add Text and Formatting to Cells in Word Tables](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [How to: Programmatically Add Rows and Columns to Word Tables](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [How to: Programmatically Populate Word Tables with Document Properties](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
