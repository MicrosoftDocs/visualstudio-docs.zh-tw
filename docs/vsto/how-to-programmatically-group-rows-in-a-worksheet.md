---
title: 如何：以程式設計方式將工作表中的資料列分組
description: 瞭解如何使用 NamedRange 控制項或原生 Excel 範圍物件，以程式設計方式將 Microsoft Excel 中的一或多個完整資料列分組。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 203ea7d17a02a224c290e5dd3c6070c06a1d26e4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525709"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>如何：以程式設計方式將工作表中的資料列分組
  您可以將一或多個整個資料列分組。 若要在工作表中建立群組，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 如果您 <xref:Microsoft.Office.Tools.Excel.NamedRange> 在設計階段將控制項加入檔層級專案中，您可以使用控制項以程式設計方式建立群組。 下列範例假設 <xref:Microsoft.Office.Tools.Excel.NamedRange> 相同的工作表上有三個控制項： `data2001` 、 `data2002` 和 `dataAll` 。 每個命名範圍都會參考工作表中的整個資料列。

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>在工作表上建立 NamedRange 控制項的群組

1. 藉由呼叫每個範圍的方法，將三個命名範圍組成群組 <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> 。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > 若要取消群組資料列，請呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> 方法。

## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍
 此程式碼假設您在 `data2001` `data2002` 工作表上有三個名為、和的 Excel 範圍 `dataAll` 。

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>若要在工作表中建立一組 Excel 範圍

1. 藉由呼叫每個範圍的方法，將三個命名範圍組成群組 <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> 。 下列範例假設在 <xref:Microsoft.Office.Interop.Excel.Range> `data2001` `data2002` `dataAll` 相同的工作表上有三個名為、和的控制項。 每個命名範圍都會參考工作表中的整個資料列。

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > 若要取消群組資料列，請呼叫 <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> 方法。

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
