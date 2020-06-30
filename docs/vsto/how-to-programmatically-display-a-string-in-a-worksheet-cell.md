---
title: 如何：以程式設計方式在工作表儲存格中顯示字串
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ed93451942ccb0376c78ebb0e99b269a658131de
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545921"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>如何：以程式設計方式在工作表儲存格中顯示字串
  這個範例示範如何以程式設計方式在儲存格中顯示文字。 若要在儲存格中顯示文字，請使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項或原生 Excel range 物件。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 這個範例會使用 <xref:Microsoft.Office.Tools.Excel.NamedRange> 名為的控制項 `message` 。 控制項必須在設計階段加入至檔層級自訂。 下列程式碼必須放在工作表類別中，而不是在 `ThisWorkbook` 類別中。

### <a name="to-display-text-in-a-namedrange-control"></a>在 NamedRange 控制項中顯示文字

1. 將控制項的值設定 <xref:Microsoft.Office.Tools.Excel.NamedRange> 為**Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>使用原生 Excel 範圍
 下列程式碼會以程式設計方式建立新範圍，然後為其指派值。

### <a name="to-display-text-in-an-excel-range"></a>若要在 Excel 範圍中顯示文字

1. 在儲存格**A1**上取出範圍 `Sheet1` ，並將值設定為**Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>另請參閱
- [逐步解說：使用 Windows form 收集資料](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office 方案疑難排解](../vsto/troubleshooting-office-solutions.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
