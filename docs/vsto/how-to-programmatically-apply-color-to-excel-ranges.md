---
title: 'How to: Programmatically Apply Color to Excel Ranges | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
ms.assetid: a9c40229-5308-459a-9216-7e13d82c7cb5
caps.latest.revision: 47
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6407cd7fee22f42eeea5f89558116291c79dd233
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>How to: Programmatically Apply Color to Excel Ranges
  To apply a color to text within a range of cells, use a <xref:Microsoft.Office.Tools.Excel.NamedRange> control or a native Excel range object.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Using a NamedRange Control  
 This example is for document-level customizations.  
  
#### <a name="to-apply-color-to-a-namedrange-control"></a>To apply color to a NamedRange control  
  
1.  Create a <xref:Microsoft.Office.Tools.Excel.NamedRange> control at cell A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]  [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Set the color of the text in the <xref:Microsoft.Office.Tools.Excel.NamedRange> control.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]  [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="using-native-excel-ranges"></a>Using Native Excel Ranges  
  
#### <a name="to-apply-color-to-a-native-excel-range-object"></a>To apply color to a native Excel range object  
  
1.  Create a range at cell A1 and then set the color of the text.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]  [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>See Also  
 [Working with Ranges](../vsto/working-with-ranges.md)   
 [NamedRange Control](../vsto/namedrange-control.md)   
 [How to: Programmatically Apply Styles to Ranges in Workbooks](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [How to: Programmatically Refer to Worksheet Ranges in Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  
