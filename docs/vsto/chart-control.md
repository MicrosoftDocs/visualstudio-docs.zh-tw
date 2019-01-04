---
title: 圖表控制項
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: edeaa0df7841795548637cabbd471daad9d2e878
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826201"
---
# <a name="chart-control"></a>圖表控制項
  <xref:Microsoft.Office.Tools.Excel.Chart> 控制項是一個會公開事件的圖表物件。 當您將圖表加入工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.Chart> 物件，以便您直接對這個物件進行程式設計，而不必周遊 Microsoft Office Excel 物件模型。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>建立控制項  
 您可以新增<xref:Microsoft.Office.Tools.Excel.Chart>Microsoft Office Excel 工作表在設計階段或在執行階段在文件層級專案中的控制項。  
  
 您可以新增<xref:Microsoft.Office.Tools.Excel.Chart>控制項加入工作表，在執行階段中的 VSTO 增益集。 如需詳細資訊，請參閱[＜How to：將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)。  
  
> [!NOTE]  
>  當工作表關閉時，動態建立的圖表物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## <a name="formatting"></a>格式化  
 可套用至 <xref:Microsoft.Office.Interop.Excel.Chart> 的任何格式，皆可套用至 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。 其包括框線、字型、圖表類型、格線、圖例和資料標籤。  
  
## <a name="events"></a>事件  
 下列事件適用於 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項：  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>另請參閱  
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何：將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
