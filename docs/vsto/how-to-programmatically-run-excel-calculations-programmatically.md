---
title: HOW TO：以程式設計方式執行 Excel 計算
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 82e2cbd2f3e74e50c7ff01f6943fdb62e11f1525
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821057"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>HOW TO：以程式設計方式執行 Excel 計算  
  您可以使用類似的程序中執行計算<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生的 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="run-calculations-in-a-namedrange-control"></a>NamedRange 控制項中執行計算  
 下列範例會建立<xref:Microsoft.Office.Tools.Excel.NamedRange>A1 儲存格，然後計算儲存格。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
### <a name="to-run-calculations-in-a-namedrange-control"></a>若要執行計算 NamedRange 控制項  
  
1.  建立具名的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]  
  
2.  呼叫<xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A>指定範圍的方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]  
  
## <a name="run-calculations-in-a-native-excel-range"></a>原生的 Excel 範圍中執行計算  
  
### <a name="to-run-calculations-in-a-native-excel-range"></a>若要在原生的 Excel 範圍中執行計算  
  
1.  建立具名的範圍。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]  
  
2.  呼叫<xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A>指定範圍的方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
