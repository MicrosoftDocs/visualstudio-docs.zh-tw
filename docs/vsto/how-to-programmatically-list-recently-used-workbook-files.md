---
title: 如何： 以程式設計方式列出最近使用之活頁簿檔案 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c2d9c333b6d96329abec3fd52ecaa5da1cf97c74
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>如何：以程式設計方式列出最近使用的活頁簿檔案
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>屬性會傳回集合，其中包含出現在 Microsoft Office Excel 檔案清單中最近使用的所有檔案的名稱。 清單的長度會根據使用者選取要保留的檔案數目而有所不同。 您可以在範圍中顯示結果。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Range 物件中的清單中最近使用過的活頁簿  
  
1.  循環的最近使用的檔案清單，並顯示名稱相對於儲存格中<xref:Microsoft.Office.Interop.Excel.Range>物件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>另請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  