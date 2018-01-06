---
title: "如何： 以程式設計方式分組的工作表中的資料列 |Microsoft 文件"
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f17c90fb5f10dfdc0658f9176e0e15cedcc6f1d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>如何：以程式設計方式在工作表中分組資料列
  您可以分組一或多個整個資料列。 若要在工作表中建立群組時，使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>使用 NamedRange 控制項  
 如果您將加入<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入文件層級專案，在設計階段，您可以使用的控制項，以程式設計方式建立群組。 下列範例假設有三個<xref:Microsoft.Office.Tools.Excel.NamedRange>相同的工作表上的控制項： `data2001`， `data2002`，和`dataAll`。 每個具名的範圍會參考工作表中的整個資料列。  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>若要建立一組工作表上的 NamedRange 控制項  
  
1.  藉由呼叫群組三個具名的範圍<xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A>每個範圍的方法。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  若要取消群組的資料列，請呼叫<xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>方法。  
  
## <a name="using-native-excel-ranges"></a>使用原生 Excel 範圍  
 此程式碼假設您有三個名為的 Excel 範圍`data2001`， `data2002`，和`dataAll`工作表上。  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>若要在工作表中建立的 Excel 範圍群組  
  
1.  藉由呼叫群組三個具名的範圍<xref:Microsoft.Office.Interop.Excel.Range.Group%2A>每個範圍的方法。 下列範例假設有三個<xref:Microsoft.Office.Interop.Excel.Range>控制項名為`data2001`， `data2002`，和`dataAll`上相同的工作表。 每個具名的範圍會參考工作表中的整個資料列。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  若要取消群組的資料列，請呼叫<xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>方法。  
  
## <a name="see-also"></a>請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何： 將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  