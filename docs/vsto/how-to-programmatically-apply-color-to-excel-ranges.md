---
title: 如何：以程式設計方式將色彩套用至 Excel 範圍
description: 瞭解如何將色彩套用至儲存格範圍內的文字，您可以使用 NamedRange 控制項或原生 Excel 範圍物件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7ab1681cf402fc45b81b49b77a84973be83729c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910101"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>如何：以程式設計方式將色彩套用至 Excel 範圍
  若要將色彩套用至儲存格範圍內的文字，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 此範例適用于檔層級自訂。

### <a name="to-apply-color-to-a-namedrange-control"></a>將色彩套用至 NamedRange 控制項

1. <xref:Microsoft.Office.Tools.Excel.NamedRange>在儲存格 A1 上建立控制項。

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. 設定控制項中文字的色彩 <xref:Microsoft.Office.Tools.Excel.NamedRange> 。

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍

### <a name="to-apply-color-to-a-native-excel-range-object"></a>將色彩套用至原生 Excel 範圍物件

1. 在儲存格 A1 上建立範圍，然後設定文字的色彩。

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [如何：以程式設計方式在程式碼中參考工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
