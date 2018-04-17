---
title: 如何： 以程式設計方式加入文字和格式在 Word 表格中的資料格 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7d50a5531bdb4e073c2760ae6d4e746b4970af6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式
  每個資料表都是由一組儲存格組成。 每個個別的 <xref:Microsoft.Office.Interop.Word.Cell> 物件各代表資料表中的一個儲存格。 您可以依據儲存格在資料表中的位置來參考每一個儲存格。 這個範例會參考位於資料表中第一列和第一欄的儲存格、將文字加入儲存格，並套用格式。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>若要將文字和格式加入儲存格  
  
1.  依據儲存格在資料表中的位置來參考儲存格、將文字加入儲存格，然後套用格式。  
  
     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用的文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何： 以程式設計方式將資料列和資料行加入至 Word 表格](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何：以程式設計方式將文件屬性填入 Word 表格](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  