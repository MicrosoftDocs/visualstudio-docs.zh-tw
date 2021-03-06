---
title: 如何：以程式設計方式在活頁簿中加入新的工作表
description: 瞭解如何以程式設計方式建立工作表，然後將工作表加入活頁簿中的工作表集合。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c093d61e38b3416fbef1e85dcf5af052c64db590
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827405"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>如何：以程式設計方式在活頁簿中加入新的工作表
  您可以用程式設計方式建立工作表，然後將工作表加入活頁簿的工作表集合。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>在文件層級自訂的活頁簿中加入新的工作表

1. 使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets> 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet15":::

     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 如果要加入 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目，您應該在設計階段加入工作表。

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>在 VSTO 增益集的活頁簿中加入新的工作表

1. 使用 <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets> 方法。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet11":::

     新的工作表是原生的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件，不是主項目。 您也可以從原生的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 物件產生 <xref:Microsoft.Office.Interop.Excel.Worksheet> 主項目。 如需詳細資訊，請參閱 [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以程式設計方式選取工作表](../vsto/how-to-programmatically-select-worksheets.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
