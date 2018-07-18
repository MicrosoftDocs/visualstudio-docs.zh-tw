---
title: 如何： 填滿 ListObject 控制項的資料
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e9e255d4099a90173b9dbc7ff6fd7b2225d0622d
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255700"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>如何： 填滿 ListObject 控制項的資料
  使用資料繫結也可以快速在文件中加入資料。 將資料繫結至清單物件之後，您可以中斷清單物件的連線，讓它顯示資料但不再繫結至資料來源。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[如何： 建立 Excel 連接到 SharePoint 清單中的清單？](http://go.microsoft.com/fwlink/?LinkID=130263)。  
  
### <a name="to-bind-data-to-a-listobject-control"></a>將資料繫結至 ListObject 控制項  
  
1.  在類別層級建立 <xref:System.Data.DataTable> 。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]  
  
2.  將範例資料行和資料加入 `Startup` 類別的 `Sheet1` 事件處理常式 (文件層級專案) 或 `ThisAddIn` 類別 (應用程式層級專案)。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]  
  
3.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 清單物件中的資料行順序可能不同於 <xref:System.Data.DataTable>中的出現順序 。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]  
  
### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>中斷 ListObject 控制項與資料來源的連線  
  
1.  呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 的 `List1`方法。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `list1` 。  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何： 對應 ListObject 資料行的資料](../vsto/how-to-map-listobject-columns-to-data.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject 控制項](../vsto/listobject-control.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 從資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何： 擴展的資料服務文件](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  