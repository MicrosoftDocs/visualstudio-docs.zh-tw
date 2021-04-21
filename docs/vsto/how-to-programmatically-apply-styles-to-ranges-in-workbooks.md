---
title: 如何：以程式設計方式將樣式套用至活頁簿中的範圍
description: 瞭解如何將命名樣式套用至活頁簿中的區域。 Excel 提供多個預先定義的樣式。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828302"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>如何：以程式設計方式將樣式套用至活頁簿中的範圍
  您可以將具名樣式套用至活頁簿中的區域。 Excel 提供多個預先定義的樣式。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 [儲存格格式]  對話方塊會顯示格式化儲存格可使用的所有選項，而且每個選項都可從程式碼取得。 若要在 Excel 中顯示這個對話方塊，請按一下 [格式]  功能表上的 [儲存格]  。

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>將樣式套用至文件層級自訂中的具名範圍

1. 建立新的樣式，並設定其屬性。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. 建立 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，為其指派文字，然後套用新的樣式。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>從文件層級自訂中的具名範圍清除樣式

1. 將內文樣式套用至範圍。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>將樣式套用到 VSTO 增益集中的具名範圍

1. 建立新的樣式，並設定其屬性。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. 建立 <xref:Microsoft.Office.Interop.Excel.Range>，為其指派文字，然後套用新的樣式。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>從 VSTO 增益集中的命名範圍清除樣式

1. 將內文樣式套用至範圍。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>另請參閱
- [使用範圍](../vsto/working-with-ranges.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
