---
title: 如何： 以程式設計方式在活頁簿中加入新的工作表 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 934b3cb9b333c1cd9c551346eb7ac30edcd5e368
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>如何：以程式設計方式在活頁簿中加入新的工作表
  您可以用程式設計方式建立工作表，然後將工作表加入活頁簿的工作表集合。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>在文件層級自訂的活頁簿中加入新的工作表  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 如果要加入 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目，您應該在設計階段加入工作表。  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>在 VSTO 增益集的活頁簿中加入新的工作表  
  
1.  使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 您也可以從原生的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 物件產生 <xref:Microsoft.Office.Interop.Excel.Worksheet> 主項目。 如需詳細資訊，請參閱 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何： 以程式設計方式從活頁簿刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何： 以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  