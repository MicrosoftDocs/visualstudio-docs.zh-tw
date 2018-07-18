---
title: 如何： 以程式設計方式分組的工作表中的資料列
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa9624f90a337fb85ba2868b3b5c4f3cb1553ffb
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35258732"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>如何： 以程式設計方式分組的工作表中的資料列
  您可以群組一個或多個完整的資料列。 若要建立群組時的工作表中，使用<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項或原生的 Excel 範圍物件。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>使用 NamedRange 控制項  
 如果您新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入文件層級專案，在設計階段，您可以使用控制項，以程式設計方式建立的群組。 下列範例假設有三個<xref:Microsoft.Office.Tools.Excel.NamedRange>相同的工作表上的控制項： `data2001`， `data2002`，和`dataAll`。 每個具名的範圍指的是工作表中的整個資料列。  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>若要建立的工作表上的 NamedRange 控制項群組  
  
1.  藉由呼叫群組三個具名的範圍<xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A>的每個範圍的方法。 這個程式碼必須放置在工作表類別中，而不是 `ThisWorkbook` 類別中。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  若要取消群組的資料列，請呼叫<xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A>方法。  
  
## <a name="use-native-excel-ranges"></a>使用原生 Excel 範圍  
 此程式碼假設您有三個名為的 Excel 範圍`data2001`， `data2002`，和`dataAll`工作表上。  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>若要在工作表中建立的 Excel 範圍群組  
  
1.  藉由呼叫群組三個具名的範圍<xref:Microsoft.Office.Interop.Excel.Range.Group%2A>的每個範圍的方法。 下列範例假設有三個<xref:Microsoft.Office.Interop.Excel.Range>控制項命名為`data2001`， `data2002`，和`dataAll`相同的工作表上。 每個具名的範圍指的是工作表中的整個資料列。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  若要取消群組的資料列，請呼叫<xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A>方法。  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [如何： 將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  