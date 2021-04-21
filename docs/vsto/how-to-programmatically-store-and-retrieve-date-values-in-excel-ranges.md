---
title: 以程式設計方式在 Excel 範圍中儲存 & 取出日期值
description: 瞭解如何使用 Visual Studio，以程式設計方式儲存和取出 Microsoft Excel 範圍中的日期值。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826235"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>如何：以程式設計方式在 Excel 範圍中儲存和取出日期值
  您可以儲存和取出 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件中的值。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 如果您使用 Visual Studio 中的 Office 開發工具，將在1/1/1900 或之後的日期值儲存在範圍內，它會儲存為 OLE Automation (OA) 格式。 您必須使用 <xref:System.DateTime.FromOADate%2A> 方法來取得 OLE Automation 的值 (OA) 日期。 如果日期早于1/1/1900，則會儲存為字串。

> [!NOTE]
> Excel 日期與前兩個月1900的 OLE Automation 日期不同。 如果已核取 [ **1904 日期系統** ] 選項，也有差異。 下列程式碼範例不會解決這些差異。

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項

- 此範例適用于檔層級自訂。 下列程式碼必須放在工作表類別中，而不是在 `ThisWorkbook` 類別中。

### <a name="to-store-a-date-value-in-a-named-range"></a>若要在命名範圍中儲存日期值

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>在儲存格 **A1** 上建立控制項。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. 將今天的日期設定為的值 `NamedRange1` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>從命名範圍中取出日期值

1. 從取得日期值 `NamedRange1` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>在原生 Excel 範圍物件中儲存日期值

1. 建立 <xref:Microsoft.Office.Interop.Excel.Range> 代表儲存格 **A1** 的。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. 將今天的日期設定為的值 `rng` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>從原生 Excel 範圍物件取出日期值

1. 從取得日期值 `rng` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
