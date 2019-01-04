---
title: HOW TO：以程式設計方式列出最近使用的活頁簿檔案
ms.date: 02/02/2017
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
ms.openlocfilehash: 850dc26b9a5f270b3806d9623795535d34cf8f4b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989612"
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>HOW TO：以程式設計方式列出最近使用的活頁簿檔案
  <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A>屬性會傳回集合，其中包含出現在 Microsoft Office Excel 清單最近使用的檔案中的所有檔案的名稱。 清單的長度會根據使用者選取要保留的檔案數目而有所不同。 您可以在範圍中顯示結果。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-recently-used-workbooks-in-a-range-object"></a>若要列出最近使用的活頁簿中的範圍物件  
  
1.  迴圈的最新的檔案清單，並顯示在相對於儲存格的名稱<xref:Microsoft.Office.Interop.Excel.Range>物件。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>另請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
