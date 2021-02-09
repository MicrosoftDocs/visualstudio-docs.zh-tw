---
title: 如何：以程式設計方式隱藏工作表
description: 瞭解如何使用工作表主專案，以程式設計方式顯示或隱藏 Microsoft Excel 活頁簿中的任何工作表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5763e040e0206272b6b50b039f1260bcbc99db49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908587"
---
# <a name="how-to-programmatically-hide-worksheets"></a>如何：以程式設計方式隱藏工作表
  您可以顯示或隱藏活頁簿中的任何工作表。 若要隱藏工作表，請使用工作表主項目，或使用活頁簿的工作表集合存取工作表。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>使用工作表主專案
 如果在文件層級自訂的設計階段即已加入工作表，請使用 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 屬性隱藏指定的工作表。

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>使用工作表主項目隱藏工作表

1. 將 <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> 主項目的 `Sheet1` 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。

     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合
 在下列情況中，透過 Microsoft Office Excel 的 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合存取工作表：

- 您想要在 VSTO 增益集中隱藏工作表。

- 您想要隱藏的工作表，是在文件層級自訂的執行階段建立的。

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>使用 Excel 活頁簿的工作表集合隱藏工作表

1. 將工作表的 <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> 屬性設定為 <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> 列舉值。

     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]

## <a name="see-also"></a>另請參閱
- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式從活頁簿中刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [如何：以程式設計方式在活頁簿內移動工作表](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [如何：以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
