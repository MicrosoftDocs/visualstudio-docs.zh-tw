---
title: HOW TO：將圖表控制項加入工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 577c0531e73ad5586386c478611e57daa7e651d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967462"
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>HOW TO：將圖表控制項加入工作表
  您可以新增<xref:Microsoft.Office.Tools.Excel.Chart>Microsoft Office Excel 工作表在設計階段，並在執行階段在文件層級自訂中的控制項。 您也可以新增<xref:Microsoft.Office.Tools.Excel.Chart>在 VSTO 增益集的執行階段的控制項。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 本主題說明下列工作：  
  
- [在設計階段加入圖表控制項](#designtime)  
  
- [在文件層級專案中的執行階段加入圖表控制項](#runtimedoclevel)  
  
- [在 VSTO 增益集專案中的執行階段加入圖表控制項](#runtimeaddin)  
  
  如需詳細資訊<xref:Microsoft.Office.Tools.Excel.Chart>控制項，請參閱[圖表控制項](../vsto/chart-control.md)。  
  
##  <a name="designtime"></a> 在設計階段加入圖表控制項  
 您可以採用您從應用程式中加入圖表的方式，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入工作表。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart>控制項不是可從**工具箱**或**Zdroje dat**視窗。  
  
### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>將圖表主控制項加入 Excel 工作表  
  
1.  在 **插入**索引標籤**圖表**群組中，按一下**資料行**，按一下圖表的類別，然後按一下 您要的圖表類型。  
  
2.  在 [**插入圖表**] 對話方塊中，按一下**確定**。  
  
3.  在 **設計**索引標籤中，於**資料**群組中，按一下**選取資料**。  
  
4.  在 **選取資料來源**對話方塊中，按一下**圖表****資料範圍**方塊，然後清除任何預設選取項目。  
  
5.  在 **圖表的資料**工作表中，選取包含圖表之資料的資料格範圍 (資料格**A5**透過**D8**)。  
  
6.  在 [**選取資料來源**] 對話方塊中，按一下**確定**。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入圖表控制項  
 您可以新增<xref:Microsoft.Office.Tools.Excel.Chart>在執行階段動態控制項。 當文件關閉時，動態建立的圖表便不再是文件中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以程式設計方式將圖表控制項加入工作表  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中插入下列程式碼，以加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中的執行階段加入圖表控制項  
 您可以利用程式設計方式，在 VSTO 增益集專案中，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入任何開啟中的工作表。 如需詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
 當工作表關閉時，動態建立的圖表控制項便不再是工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>以程式設計方式將圖表控制項加入工作表  
  
1.  下列程式碼會產生開啟中之工作表的主項目，然後新增 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 此範例需要：  
  
-   要繪製成圖表的資料，即工作表中 A5 到 D8 之間的範圍。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [圖表控制項](../vsto/chart-control.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
