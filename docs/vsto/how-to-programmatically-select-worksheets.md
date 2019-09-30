---
title: 作法：以程式設計方式選取工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255621"
---
# <a name="how-to-programmatically-select-worksheets"></a>HOW TO：以程式設計方式選取工作表
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> 方法會選取指定的物件，將使用者選取的項目移到新物件。 如果您要將焦點置於這個物件而不變更使用者的選取範圍，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> 方法。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 如果要選取 VSTO 增益集中的現有工作表，或者該工作表是在執行階段於文件層級自訂中所建立，則您必須使用 Excel 活頁簿的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取該工作表，否則就要直接存取 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。

## <a name="use-the-worksheet-host-item"></a>使用工作表主專案
 在檔層級自訂中，將下列程式碼加入至*Sheet1 .vb*或*Sheet1.cs*。

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
