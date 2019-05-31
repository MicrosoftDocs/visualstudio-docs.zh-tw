---
title: 新增文字以程式設計的方式格式化為 Word 表格儲存格
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdab1877cf2114f7828dbd65786cf8758d77d0f3
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402021"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>HOW TO：以程式設計方式加入文字和格式在 Word 表格的儲存格
  每個資料表都是由一組儲存格組成。 每個個別的 <xref:Microsoft.Office.Interop.Word.Cell> 物件各代表資料表中的一個儲存格。 您可以依據儲存格在資料表中的位置來參考每一個儲存格。 這個範例會參考位於資料表中第一列和第一欄的儲存格、將文字加入儲存格，並套用格式。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>若要將文字和格式加入儲存格

1. 依據儲存格在資料表中的位置來參考儲存格、將文字加入儲存格，然後套用格式。

     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)
- [如何：以程式設計方式將資料列和資料行加入至 Word 表格](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [如何：以程式設計方式填入 Word 表格文件屬性](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
