---
title: 如何：以程式設計方式在程式碼中參考工作表範圍
description: 瞭解如何使用 Visual Studio，以程式設計方式參考 Microsoft Excel 工作表中 NamedRange 控制項或原生 Excel 範圍物件的內容。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89a4b7c594f942405777145f94ed0a3503e9b16f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963753"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>如何：以程式設計方式在程式碼中參考工作表範圍
  您可以使用類似的進程來參考 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件的內容。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 下列範例會將加入 <xref:Microsoft.Office.Tools.Excel.NamedRange> 至工作表，然後將文字加入至範圍中的儲存格。

### <a name="to-refer-to-a-namedrange-control"></a>參考 NamedRange 控制項

1. 將字串指派給 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 控制項的屬性 <xref:Microsoft.Office.Tools.Excel.NamedRange> 。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍
 下列範例會將原生 Excel 範圍加入至工作表，然後將文字加入至範圍中的儲存格。

### <a name="to-refer-to-a-native-range-object"></a>參考原生範圍物件

1. 將字串指派給 <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> 範圍的屬性。

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [如何：以程式設計方式檢查工作表中的拼寫](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [如何：以程式設計方式自動以累加方式變更資料填滿範圍](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [如何：以程式設計方式在工作表範圍中搜尋文字](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
