---
title: 如何：以程式設計方式選取工作表
description: 使用 Visual Studio，以程式設計方式使用 Excel 活頁簿的工作表主專案或工作表集合來選取 Microsoft Excel 工作表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a58c4cc53597714eb65010c2fdbb423dd20a35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899395"
---
# <a name="how-to-programmatically-select-worksheets"></a>如何：以程式設計方式選取工作表
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 方法會選取指定的物件，將使用者選取的項目移到新物件。 如果您要將焦點置於這個物件而不變更使用者的選取範圍，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> 方法。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 如果您想要在 VSTO 增益集中選取現有的工作表，或在執行時間于檔層級自訂中建立工作表，您必須使用 Excel 活頁簿的 Excel 集合來存取該工作表 <xref:Microsoft.Office.Interop.Excel.Sheets> ; 否則，您可以直接存取 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主專案。

## <a name="use-the-worksheet-host-item"></a>使用工作表主專案
 在檔層級自訂中，將下列程式碼加入至 *Sheet1* 或 *Sheet1.cs*。

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>使用主項目選取活頁簿中的第一個工作表

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 的 `Sheet1`方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合
 請使用 Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表。

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的 Sheets 集合選取活頁簿中的第一份工作表

1. 請呼叫 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的 <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> 方法，選取現用活頁簿中的第一份工作表。

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式列印工作表](../vsto/how-to-programmatically-print-worksheets.md)
- [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)
- [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [工作表主專案](../vsto/worksheet-host-item.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
