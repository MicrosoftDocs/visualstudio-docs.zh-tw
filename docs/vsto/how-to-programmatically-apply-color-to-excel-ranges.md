---
title: HOW TO：以程式設計方式將色彩套用至 Excel 範圍
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 83a7a3e58212b0c20264b3b325f3658760aa5ae4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868166"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>HOW TO：以程式設計方式將色彩套用至 Excel 範圍
  若要將色彩套用至資料格範圍內的文字，使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生的 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項  
 這個範例是用於文件層級自訂。  
  
### <a name="to-apply-color-to-a-namedrange-control"></a>若要將色彩套用到 NamedRange 控制項  
  
1.  建立<xref:Microsoft.Office.Tools.Excel.NamedRange>A1 儲存格的控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  設定中的文字色彩<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍  
  
### <a name="to-apply-color-to-a-native-excel-range-object"></a>若要將色彩套用至原生的 Excel 範圍物件  
  
1.  建立在儲存格 A1 的範圍，然後將 文字的色彩。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何：以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何：以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
