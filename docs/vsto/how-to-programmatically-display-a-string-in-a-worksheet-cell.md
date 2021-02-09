---
title: 如何：以程式設計方式在工作表儲存格中顯示字串
description: 瞭解如何使用 NamedRange 控制項或原生 Excel 範圍物件，以程式設計方式在 Microsoft Excel 工作表儲存格中顯示字串。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5a89716797ec460b461f79c94df8cea475532a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885556"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>如何：以程式設計方式在工作表儲存格中顯示字串
  此範例示範如何以程式設計方式顯示儲存格中的文字。 若要在儲存格中顯示文字，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel 範圍物件。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 這個範例會使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 名為的控制項 `message` 。 您必須在設計階段將控制項加入檔層級自訂中。 下列程式碼必須放在工作表類別中，而不是在 `ThisWorkbook` 類別中。

### <a name="to-display-text-in-a-namedrange-control"></a>在 NamedRange 控制項中顯示文字

1. 將控制項的值設定 <xref:Microsoft.Office.Tools.Excel.NamedRange> 為 **Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>使用原生 Excel 範圍
 下列程式碼會以程式設計方式建立新範圍，然後將值指派給它。

### <a name="to-display-text-in-an-excel-range"></a>在 Excel 範圍中顯示文字

1. 取出儲存格 **A1** 上的範圍 `Sheet1` ，並將值設定為 **Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>另請參閱
- [逐步解說：使用 Windows form 收集資料](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [針對 Office 方案進行疑難排解](../vsto/troubleshooting-office-solutions.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
