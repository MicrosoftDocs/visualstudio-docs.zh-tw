---
title: "如何： 以程式設計的方式排序工作表中的資料 |Microsoft 文件"
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
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
ms.assetid: 2fbc6e63-02ea-4624-8d6f-bed60e06c61e
caps.latest.revision: "56"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 211a357095290f8f8d608d01c093cd373c7525ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>如何：以程式設計方式在工作表中排序資料
  您可以在執行階段排序工作表範圍和清單中包含的資料。 下列程式碼會先按第一個資料行的資料，再按第二個資料行的資料，排序名為 `Fruits` 的多欄範圍。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="sorting-data-in-a-document-level-customization"></a>排序文件層級自訂的資料  
  
#### <a name="to-sort-data-in-a-namedrange-control"></a>排序 NamedRange 控制項的資料  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> 方法。 下列範例需要工作表上名為 `Fruits` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
     [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]  
  
 將下列程式碼放在 Sheet1.vb 或 Sheet1.cs 中，以排序 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中的資料。 此程式碼假設您在名為 `Sheet1` 的工作表中，有名為 `fruitList` 的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>排序 ListObject 控制項的資料  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject> 主控制項 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 屬性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]  
  
## <a name="sorting-data-in-a-vsto-add-in"></a>排序 VSTO 增益集的資料  
  
#### <a name="to-sort-data-in-a-native-range"></a>排序原生範圍的資料  
  
1.  呼叫原生 Excel <xref:Microsoft.Office.Interop.Excel.Range> 控制項的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。 下列範例需要工作表上名為 `Fruits` 的原生 Excel 控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]  
  
#### <a name="to-sort-data-in-a-listobject-control"></a>排序 ListObject 控制項的資料  
  
1.  呼叫原生 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控制項 <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> 屬性的 <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> 方法。 下列範例假設使用中工作表有名為 `fruitList` 的原生 Excel <xref:Microsoft.Office.Interop.Excel.ListObject> 控制項。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計的方式自動填滿範圍與以累加方式變更資料](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [如何： 以程式設計方式參考程式碼中的工作表範圍](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [如何： 以程式設計方式將樣式套用至活頁簿中的範圍](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  