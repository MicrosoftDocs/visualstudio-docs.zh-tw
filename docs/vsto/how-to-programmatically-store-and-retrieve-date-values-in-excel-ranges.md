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
ms.openlocfilehash: 892f8db0a6cbeee485c8139c2d6e4614f17c1cc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899412"
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

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. 將今天的日期設定為的值 `NamedRange1` 。

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>從命名範圍中取出日期值

1. 從取得日期值 `NamedRange1` 。

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>在原生 Excel 範圍物件中儲存日期值

1. 建立 <xref:Microsoft.Office.Interop.Excel.Range> 代表儲存格 **A1** 的。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. 將今天的日期設定為的值 `rng` 。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>從原生 Excel 範圍物件取出日期值

1. 從取得日期值 `rng` 。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
