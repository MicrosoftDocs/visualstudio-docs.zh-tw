---
title: HOW TO：以程式設計方式參考程式碼中的工作表範圍
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b1a1f0f6c37bca2d545e3b689bc72c553ffc6c6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867135"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>HOW TO：以程式設計方式參考程式碼中的工作表範圍
  您可以使用類似的程序來參考的內容<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生的 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項  
 下列範例會將<xref:Microsoft.Office.Tools.Excel.NamedRange>加入工作表，然後新增至範圍的儲存格的文字。  
  
### <a name="to-refer-to-a-namedrange-control"></a>若要參考 NamedRange 控制項  
  
1.  將字串指派給<xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>屬性<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍  
 下列範例會將原生的 Excel 範圍加入至工作表，並再將文字加入至範圍中的資料格。  
  
### <a name="to-refer-to-a-native-range-object"></a>若要參考原生的範圍物件  
  
1.  指派字串給<xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>範圍的屬性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何：以程式設計方式檢查工作表拼字](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：使用累加式變更資料，以程式設計的方式自動填滿範圍](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何：以程式設計方式在工作表範圍中的文字搜尋](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
