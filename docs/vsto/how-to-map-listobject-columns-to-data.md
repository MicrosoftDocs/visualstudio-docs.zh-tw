---
title: HOW TO：將 ListObject 欄對應到資料
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a37c0f12943d60f67ee0d17b15315ac85af509d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967881"
---
# <a name="how-to-map-listobject-columns-to-data"></a>HOW TO：將 ListObject 欄對應到資料
  當您將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項繫結到 <xref:System.Data.DataTable>時，您可能不想在清單中顯示所有資料行，或可能有某些資料行未繫結至資料。 當您呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject> 方法時，您可以對應想要顯示在 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 的資料行。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:在連接至 SharePoint 清單的 Excel 中建立清單嗎？](http://go.microsoft.com/fwlink/?LinkID=130263).

## <a name="map-columns"></a>將資料行對應

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>對應資料表和清單中的資料行

1. 在類別層級建立 <xref:System.Data.DataTable> 。

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. 新增範例資料行和資料`Startup`事件處理常式`Sheet1`類別 （在文件層級專案中） 或`ThisAddIn`類別 （在 VSTO 增益集專案中）。

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. 呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 將繫結的清單物件來新建<xref:System.Data.DataTable>，但它們在出現的順序不同的清單物件中的資料行的順序<xref:System.Data.DataTable>。

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>指定未對應的資料行
 當您將資料行對應至 <xref:System.Data.DataTable>時，您也可以透過傳入空字串，指定某些資料行不應該繫結至資料。 不繫結至資料的新資料行，就會加入 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>對應 ListObject 資料行時指定未對應的資料行

1. 呼叫 <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> 方法並按應用的順序傳入資料行名稱。 使用空字串表示該處加入了未對應的資料行，本例為介於標題資料行和姓氏資料行之間。

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>編譯程式碼
 這個程式碼範例假設在這個程式碼出現的工作表中已有名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `list1` 。

## <a name="see-also"></a>另請參閱
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：使用資料填入 ListObject 控制項](../vsto/how-to-fill-listobject-controls-with-data.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject 控制項](../vsto/listobject-control.md)
