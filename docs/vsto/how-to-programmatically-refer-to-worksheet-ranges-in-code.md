---
title: "如何： 以程式設計方式參考程式碼中的工作表範圍 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
ms.assetid: 113633b8-426a-4d02-b6b8-d459d1f110ea
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa76eff8719242d0fa3e059ad325dbdfb587f2bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>如何：以程式設計方式在程式碼中參考工作表範圍
  您使用類似的程序的內容是指<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>使用 NamedRange 控制項  
 下列範例會將<xref:Microsoft.Office.Tools.Excel.NamedRange>加入工作表，然後新增文字範圍的儲存格。  
  
#### <a name="to-refer-to-a-namedrange-control"></a>指將 NamedRange 控制項  
  
1.  指派字串給<xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>屬性<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>使用原生 Excel 範圍  
 下列範例將原生 Excel 範圍加入至工作表，然後將文字加入儲存格範圍中。  
  
#### <a name="to-refer-to-a-native-range-object"></a>若要參考原生範圍物件  
  
1.  指派字串給<xref:Microsoft.Office.Interop.Excel.Range.Value2%2A>範圍的屬性。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>另請參閱  
 [使用範圍](../vsto/working-with-ranges.md)   
 [如何： 以程式設計方式檢查工作表拼字](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [如何： 以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [如何： 以程式設計的方式自動填滿範圍與以累加方式變更資料](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何： 以程式設計方式搜尋工作表範圍中的文字](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  