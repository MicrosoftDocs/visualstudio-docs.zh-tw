---
title: HOW TO：以程式設計方式在工作表儲存格中顯示字串
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7d391022e9ce86b2866d941d8c0b56e2e35e3776
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629439"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>HOW TO：以程式設計方式在工作表儲存格中顯示字串
  此範例示範如何以程式設計方式顯示在資料格中的文字。 若要在儲存格中顯示文字，使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生的 Excel 範圍物件。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項
 這個範例會使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`message`。 必須將控制項加入至文件層級自訂在設計階段。 下列程式碼必須放置在工作表類別中，不在`ThisWorkbook`類別。

### <a name="to-display-text-in-a-namedrange-control"></a>NamedRange 控制項中顯示文字

1.  設定的值<xref:Microsoft.Office.Tools.Excel.NamedRange>若要控制**Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>使用原生的 Excel 範圍
 下列程式碼以程式設計方式建立新的範圍，然後將值指派給它。

### <a name="to-display-text-in-an-excel-range"></a>若要顯示在 Excel 範圍中的文字

1.  擷取儲存格範圍**A1**上`Sheet1`並將值設定為**Hello World**。

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>另請參閱
- [逐步解說：使用 Windows form 收集資料](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Office 方案進行疑難排解](../vsto/troubleshooting-office-solutions.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
