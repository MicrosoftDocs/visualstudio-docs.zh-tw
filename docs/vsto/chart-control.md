---
title: Chart 控制項
description: 瞭解當您將圖表加入至工作表時，Visual Studio 會建立可以直接進行程式設計的圖表物件。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3530e0821d4569381f610f44ae541c04b484b469
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903781"
---
# <a name="chart-control"></a>Chart 控制項
  <xref:Microsoft.Office.Tools.Excel.Chart> 控制項是一個會公開事件的圖表物件。 當您將圖表加入工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.Chart> 物件，以便您直接對這個物件進行程式設計，而不必周遊 Microsoft Office Excel 物件模型。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>建立控制項
 您可以在 <xref:Microsoft.Office.Tools.Excel.Chart> 設計階段或執行時間于檔層級專案中，將控制項加入 Microsoft Office Excel 工作表。

 在 VSTO 增益集中，您可以在執行階段將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入工作表。 如需詳細資訊，請參閱 [如何：將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)。

> [!NOTE]
> 當工作表關閉時，動態建立的圖表物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

## <a name="formatting"></a>格式化
 可套用至 <xref:Microsoft.Office.Interop.Excel.Chart> 的任何格式，皆可套用至 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。 其包括框線、字型、圖表類型、格線、圖例和資料標籤。

## <a name="events"></a>事件
 下列事件適用於 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項：

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>另請參閱
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [如何：將圖表控制項加入至工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
