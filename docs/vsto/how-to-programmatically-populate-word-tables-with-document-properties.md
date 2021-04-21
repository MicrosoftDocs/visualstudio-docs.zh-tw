---
title: 以程式設計方式將文件屬性填入 Word 表格
description: 瞭解如何使用 Visual Studio 以程式設計方式，在 Microsoft Word 檔中將文件屬性填入資料表。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document properties, inserting in Word tables
- documents [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5cb9303e7891ec6657d0fa599921d37a184073f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827245"
---
# <a name="how-to-programmatically-populate-word-tables-with-document-properties"></a>如何：以程式設計方式將文件屬性填入 Word 表格
  下列範例會在文件的頂端建立 Microsoft Office Word 表格，並用主文件的屬性填入這個表格。

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="populate-tables-in-a-document-level-customization"></a>在檔層級自訂中填入資料表

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>建立表格並且用文件的屬性填入這個表格

1. 將範圍設為文件頂端。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet90":::

2. 插入表格標題並且包含段落標記。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet91":::

3. 在文件的該範圍內加入表格。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet92":::

4. 格式化表格並套用樣式。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet93":::

5. 將文件屬性插入儲存格。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet94":::

   下列範例示範完整的程序。 若要使用此程式碼，請從專案的 `ThisDocument` 類別中執行它。

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet89":::

## <a name="populate-tables-in-a-vsto-add-in"></a>在 VSTO 增益集中填入資料表

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>建立表格並且用文件的屬性填入這個表格

1. 將範圍設為文件頂端。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet90":::

2. 插入表格標題並且包含段落標記。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet91":::

3. 在文件的該範圍內加入表格。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet92":::

4. 格式化表格並套用樣式。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet93":::

5. 將文件屬性插入儲存格。

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet94":::

   下列範例示範完整的程序。 若要使用此程式碼，請從專案的 `ThisAddIn` 類別中執行它。

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet89":::

## <a name="see-also"></a>另請參閱
- [如何：以程式設計方式建立 Word 表格](../vsto/how-to-programmatically-create-word-tables.md)
- [如何：以程式設計方式在 Word 表格的儲存格中加入文字和格式](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [如何：以程式設計方式將資料列和資料行加入至 Word 資料表](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
