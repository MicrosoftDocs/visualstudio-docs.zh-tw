---
title: 如何： 將 ListObject 控制項加入工作表
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 402e7f80ea208d714b31bd61e25b352494310487
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949249"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>如何： 將 ListObject 控制項加入工作表
  您可以新增<xref:Microsoft.Office.Tools.Excel.ListObject>Microsoft Office Excel 工作表在設計階段，並在執行階段在文件層級專案中的控制項。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 您也可以新增<xref:Microsoft.Office.Tools.Excel.ListObject>在 VSTO 增益集專案中的執行階段的控制項。  
  
 本主題說明下列工作：  
  
- [在設計階段加入 ListObject 控制項](#designtime)  
  
- [在文件層級專案中的執行階段加入 ListObject 控制項](#runtimedoclevel)  
  
- [在 VSTO 增益集專案中的執行階段加入 ListObject 控制項](#runtimeaddin)  
  
  如需詳細資訊<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，請參閱[ListObject 控制項](../vsto/listobject-control.md)。  
  
##  <a name="designtime"></a> 在設計階段加入 ListObject 控制項  
 有幾種方式可在文件層級專案中，於設計階段將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入工作表：在 Excel 中、透過 Visual Studio 的 [工具箱] ，以及透過 [資料來源]  視窗。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-use-the-ribbon-in-excel"></a>使用 Excel 中的功能區  
  
1.  在 [插入]  索引標籤上，按一下 [表格]  群組中的 [表格] 。  
  
2.  選取您要包含在清單中的一或多個儲存格，然後按一下 [確定] 。  
  
#### <a name="to-use-the-toolbox"></a>使用工具箱  
  
1.  從 [工具箱]  的 [Excel 控制項] 索引標籤中，將 <xref:Microsoft.Office.Tools.Excel.ListObject> 拖曳至工作表。  
  
     [加入 ListObject 控制項]  對話方塊隨即出現。  
  
2.  選取您要包含在清單中的一或多個儲存格，然後按一下 [確定] 。  
  
     如果您不想保留預設名稱，您可以在 [屬性]  視窗中變更名稱。  
  
#### <a name="to-use-the-data-sources-window"></a>使用資料來源視窗  
  
1.  開啟 [資料來源]  視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。  
  
2.  將資料表從 [資料來源]  視窗拖曳至您的工作表。  
  
     繫結至資料的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項隨即加入工作表。 如需詳細資訊，請參閱 <<c0> [ 資料繫結和 Windows Form](/dotnet/framework/winforms/data-binding-and-windows-forms)。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入 ListObject 控制項  
 您可以新增<xref:Microsoft.Office.Tools.Excel.ListObject>在執行階段動態控制項。 如此可讓您建立主控制項，以回應事件。 當工作表關閉時，動態建立的清單物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>以程式設計方式將 ListObject 控制項加入工作表  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 的 `Sheet1`事件處理常式中插入下列程式碼，將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入儲存格 **A1** 至 **A4**。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中的執行階段加入 ListObject 控制項  
 您可以利用程式設計方式，在 VSTO 增益集專案中，將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入任何開啟中的工作表。 當工作表儲存並關閉時，動態建立的清單物件不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 <<c0> [ 擴充 Word 文件和 VSTO 增益集在執行階段中的 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>以程式設計方式將 ListObject 控制項加入工作表  
  
1.  下列程式碼會產生以開啟的工作表為基礎的工作表主項目，然後將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入儲存格 **A1** 至 **A4**。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何： 調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  