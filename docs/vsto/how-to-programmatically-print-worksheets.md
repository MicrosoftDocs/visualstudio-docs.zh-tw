---
title: 如何：以程式設計方式列印工作表
description: 瞭解如何使用 Visual Studio，以程式設計方式列印 Microsoft Excel 活頁簿中的任何工作表。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523764"
---
# <a name="how-to-programmatically-print-worksheets"></a>如何：以程式設計方式列印工作表

您可以列印活頁簿中的任何工作表。

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>在檔層級自訂中列印工作表

### <a name="to-print-a-worksheet"></a>列印工作表

1. 呼叫 `Sheet1` 的 `PrintOut` 方法，要求兩個複本，以及在列印前先預覽文件。

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>方法可讓您在 [**預覽列印**] 視窗中顯示指定的物件。 下列程式碼假設您有名為 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。

### <a name="to-preview-a-page-before-printing"></a>在列印前先預覽頁面

1. 呼叫工作表的 <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>在 VSTO 增益集中列印工作表

### <a name="to-print-a-worksheet"></a>列印工作表

1. 呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> 方法，要求兩個複本，以及在列印前先預覽文件。

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>方法可讓您在 [**預覽列印**] 視窗中顯示指定的物件。

### <a name="to-preview-a-page-before-printing"></a>在列印前先預覽頁面

1. 呼叫使用中工作表的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法。

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>另請參閱

- [使用工作表](../vsto/working-with-worksheets.md)
- [如何：以程式設計方式檢查工作表中的拼寫](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [工作表主專案](../vsto/worksheet-host-item.md)
- [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)
