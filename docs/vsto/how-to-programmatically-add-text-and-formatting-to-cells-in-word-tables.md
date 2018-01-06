---
title: "如何： 以程式設計方式加入文字和格式在 Word 表格中的資料格 |Microsoft 文件"
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
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
ms.assetid: 3df6492a-dc9c-43ac-8fc3-0f944edd88b2
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ed593a9d03093fa092c97ce005ca190b5c433c8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>請參閱  
 [如何： 以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)   
 [如何： 以程式設計方式將資料列和資料行加入至 Word 表格](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [如何：以程式設計方式將文件屬性填入 Word 表格](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  