---
title: 如何：以程式設計方式執行 Excel 計算
description: 瞭解如何使用 Visual Studio，以程式設計方式在 Microsoft Excel 活頁簿中執行計算。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823960"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>如何：以程式設計方式執行 Excel 計算
  您可以使用類似的進程，在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件中執行計算。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>在 NamedRange 控制項中執行計算
 下列範例會 <xref:Microsoft.Office.Tools.Excel.NamedRange> 在儲存格 A1 上建立，然後計算儲存格。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

### <a name="to-run-calculations-in-a-namedrange-control"></a>在 NamedRange 控制項中執行計算

1. 建立已命名的範圍。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. 呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> 指定範圍的方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>在原生 Excel 範圍中執行計算

### <a name="to-run-calculations-in-a-native-excel-range"></a>在原生 Excel 範圍中執行計算

1. 建立已命名的範圍。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. 呼叫 <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> 指定範圍的方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
