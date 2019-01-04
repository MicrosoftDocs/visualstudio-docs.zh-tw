---
title: HOW TO：調整 ListObject 控制項的大小
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e655305400915f1ac97a042ac1cca26e52a05ec5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909680"
---
# <a name="how-to-resize-listobject-controls"></a>HOW TO：調整 ListObject 控制項的大小
  在將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入 Microsoft Office Excel 活頁簿時，會設定該控制項的大小，不過也可以稍後再進行調整。 例如，您可能想要將兩個資料行的清單變更為三個資料行。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 您可以調整大小<xref:Microsoft.Office.Tools.Excel.ListObject>控制項在設計階段或在執行階段在文件層級專案中。 您可以調整大小<xref:Microsoft.Office.Tools.Excel.ListObject>在 VSTO 增益集專案中的執行階段的控制項。  
  
 本主題說明下列工作：  
  
- [在設計階段調整 ListObject 控制項](#designtime)  
  
- [調整 ListObject 控制項，在文件層級專案中的執行階段的大小](#runtimedoclevel)  
  
- [調整 ListObject 控制項，在 VSTO 增益集專案中的執行階段的大小](#runtimeaddin)  
  
  如需詳細資訊<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，請參閱[ListObject 控制項](../vsto/listobject-control.md)。  
  
  ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:資料行加入資料繫結清單物件，在執行階段？](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> 在設計階段調整 ListObject 控制項  
 若要調整清單的大小，您可以按一下並拖曳其中一個調整大小控點，或是在 [調整清單大小]  對話方塊中重新定義其大小。  
  
### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>使用 [調整清單大小] 對話方塊調整清單的大小  
  
  
1.  在任何地方按一下<xref:Microsoft.Office.Tools.Excel.ListObject>資料表。 **資料表工具** > **設計**功能區中的索引標籤會出現。  
  
2.  在 [屬性] 區段中，按一下**調整大小的資料表**。  

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)
  
3.  選取新的資料範圍，為您的資料表。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
##  <a name="runtimedoclevel"></a> 調整 ListObject 控制項在文件層級專案中的執行階段  
 您可以調整大小<xref:Microsoft.Office.Tools.Excel.ListObject>在執行階段使用控制項<xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>方法。 您無法使用此方法將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項移至工作表上的新位置。 標頭必須留在相同的資料列，且已調整大小的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項必須與原始的清單物件重疊。 已調整大小的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項必須包含標頭資料列，和至少一個資料列。  
  
### <a name="to-resize-a-list-object-programmatically"></a>以程式設計方式調整清單物件的大小  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上建立跨越資料格 **A1** 到 **B3** 的 `Sheet1`。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]  
  
2.  將清單大小調整成包含儲存格 **A1** 到 **C5**。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> 調整在 VSTO 增益集專案中的執行階段 ListObject 的大小  
 您可以調整大小<xref:Microsoft.Office.Tools.Excel.ListObject>控制項上任何開啟的工作表，在執行階段。 如需有關如何新增<xref:Microsoft.Office.Tools.Excel.ListObject>控制項加入工作表使用 VSTO 增益集，請參閱[How to:將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)。  
  
### <a name="to-resize-a-list-object-programmatically"></a>以程式設計方式調整清單物件的大小  
  
1.  在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上建立跨越資料格 **A1** 到 **B3** 的 `Sheet1`。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]  
  
2.  將清單大小調整成包含儲存格 **A1** 到 **C5**。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [如何：將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [如何：調整書籤控制項的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)  
