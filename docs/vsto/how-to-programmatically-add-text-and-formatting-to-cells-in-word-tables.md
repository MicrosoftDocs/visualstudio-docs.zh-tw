---
title: 以程式設計方式將文字 & 格式新增至 Word 表格儲存格
description: 瞭解如何以程式設計的方式，將文字和格式加入 Microsoft Office Word 資料表中的資料格。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 58c9e7f7d5537e4b052a732a85ad9d1c7298afa0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828393"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式
  每個資料表都是由一組儲存格組成。 每個個別的 <xref:Microsoft.Office.Interop.Word.Cell> 物件各代表資料表中的一個儲存格。 您可以依據儲存格在資料表中的位置來參考每一個儲存格。 這個範例會參考位於資料表中第一列和第一欄的儲存格、將文字加入儲存格，並套用格式。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>若要將文字和格式加入儲存格

1. 依據儲存格在資料表中的位置來參考儲存格、將文字加入儲存格，然後套用格式。

     下列程式碼範例可用於文件層級自訂。 若要使用此範例，請從專案的 `ThisDocument` 類別中執行。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     下列程式碼範例可用於 VSTO 增益集。 本範例使用現用文件。 若要使用此範例，請從專案的 `ThisAddIn` 類別中執行。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)
- [如何：以程式設計方式將資料列和資料行加入至 Word 資料表](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [如何：以程式設計方式將文件屬性填入 Word 表格](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
