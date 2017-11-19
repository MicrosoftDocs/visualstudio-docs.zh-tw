---
title: "圖表控制項 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15583118629a5b75854c87892ccc85db59d49322
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="chart-control"></a>Chart Control
  <xref:Microsoft.Office.Tools.Excel.Chart> 控制項是一個會公開事件的圖表物件。 當您將圖表加入工作表時，Visual Studio 會建立 <xref:Microsoft.Office.Tools.Excel.Chart> 物件，以便您直接對這個物件進行程式設計，而不必周遊 Microsoft Office Excel 物件模型。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>建立控制項  
 您可以透過文件層級專案，在設計階段或執行階段將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入 Microsoft Office Excel 工作表。  
  
 在 VSTO 增益集中，您可以在執行階段將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入工作表。 如需詳細資訊，請參閱[How to： 將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)。  
  
> [!NOTE]  
>  當工作表關閉時，動態建立的圖表物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
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
 [在執行階段擴充 Word 文件和 Excel 活頁簿，在 VSTO 增益集](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [在執行階段將控制項加入 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [如何： 將圖表控制項加入工作表](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  