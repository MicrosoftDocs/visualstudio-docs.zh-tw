---
title: HOW TO：使用資料填入 ListObject 控制項
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f65f6de7cfb336eb001de47fb6562b7200391419
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050097"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>HOW TO：使用資料填入 ListObject 控制項
  使用資料繫結也可以快速在文件中加入資料。 將資料繫結至清單物件之後，您可以中斷清單物件的連線，讓它顯示資料但不再繫結至資料來源。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:在連接至 SharePoint 清單的 Excel 中建立清單嗎？](http://go.microsoft.com/fwlink/?LinkID=130263).

### <a name="to-bind-data-to-a-listobject-control"></a>將資料繫結至 ListObject 控制項

1. 在類別層級建立 <xref:System.Data.DataTable> 。

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2. 將範例資料行和資料加入 `Startup` 類別的 `Sheet1` 事件處理常式 (文件層級專案) 或 `ThisAddIn` 類別 (應用程式層級專案)。

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3. 呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 清單物件中的資料行順序可能不同於 <xref:System.Data.DataTable>中的出現順序 。

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>中斷 ListObject 控制項與資料來源的連線

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> 的 `List1`方法。

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>編譯程式碼
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `list1` 。

## <a name="see-also"></a>另請參閱
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：將 ListObject 欄對應到資料](../vsto/how-to-map-listobject-columns-to-data.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject 控制項](../vsto/listobject-control.md)
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：從資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [如何：服務中的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)
