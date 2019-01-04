---
title: HOW TO：將 NamedRange 控制項加入工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1d9515f5a42d37d73a95460fa458090992c488aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928655"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>HOW TO：將 NamedRange 控制項加入工作表
  您可以新增<xref:Microsoft.Office.Tools.Excel.NamedRange>Microsoft Office Excel 工作表在設計階段，並在執行階段在文件層級專案中的控制項。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 您也可以新增<xref:Microsoft.Office.Tools.Excel.NamedRange>在 VSTO 增益集專案中的執行階段的控制項。  
  
 本主題說明下列工作：  
  
- [在設計階段加入 NamedRange 控制項](#designtime)  
  
- [在文件層級專案中的執行階段加入 NamedRange 控制項](#runtimedoclevel)  
  
- [在 VSTO 增益集專案中的執行階段加入 NamedRange 控制項](#runtimeaddin)  
  
  如需詳細資訊<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，請參閱[NamedRange 控制項](../vsto/namedrange-control.md)。  
  
##  <a name="designtime"></a> 在設計階段加入 NamedRange 控制項  
 有幾種方式可在文件層級專案中，於設計階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入工作表：在 Excel 中、透過 Visual Studio 的 [工具箱] ，以及透過 [資料來源]  視窗。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>使用 Excel 中的名稱方塊將 NamedRange 控制項加入工作表  
  
1.  選取您要包含在指定範圍中的一或多個儲存格。  
  
2.  在 [**名稱] 方塊**，輸入的名稱範圍並按下**Enter**。  
  
     [名稱方塊]  位於工作表 **A** 欄正上方的公式列旁。  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>使用工具箱將 NamedRange 控制項加入工作表  
  
1.  開啟 [工具箱]  ，然後按一下 [Excel 控制項]  索引標籤。  
  
2.  按一下 <xref:Microsoft.Office.Tools.Excel.NamedRange> 並將拖曳至工作表。  
  
     [加入指定範圍]  對話方塊隨即出現。  
  
3.  選取您要包含在指定範圍中的一或多個儲存格。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
     如果您不想要使用指定給控制項的預設名稱，您可以在 [屬性]  視窗中變更名稱。  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>使用資料來源視窗將 NamedRange 控制項加入工作表  
  
1.  開啟 [資料來源]  視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。  
  
2.  將單一欄位從 [資料來源]  視窗拖曳至您的工作表。  
  
     繫結至資料的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項隨即加入工作表。 如需詳細資訊，請參閱 <<c0> [ 資料繫結和 Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms)。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入 NamedRange 控制項  
 您可以新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項以程式設計方式加入工作表，在執行階段。 如此可讓您建立主控制項，以回應事件。 當工作表關閉時，動態建立的指定範圍不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>以程式設計方式將 NamedRange 控制項加入工作表  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 的 `Sheet1`事件處理常式中插入下列程式碼，以將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入儲存格 **A1** 並將其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性設定為 `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中的執行階段加入 NamedRange 控制項  
 您可以利用程式設計方式，在 VSTO 增益集專案中，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入任何開啟中的工作表。 當工作表關閉時，動態建立的指定範圍不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>以程式設計方式將 NamedRange 控制項加入工作表  
  
1.  下列程式碼會產生以開啟的工作表為基礎的工作表主項目，然後將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入儲存格 **A1** 並將其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性設定為 `Hello world`。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
