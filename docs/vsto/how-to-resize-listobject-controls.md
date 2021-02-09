---
title: 如何：調整 ListObject 控制項的大小
description: 瞭解如何使用 Visual Studio 以程式設計方式調整 Microsoft Excel 活頁簿中 ListObject 控制項的大小。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- ListObject control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e839e253e54e7c9c0358bef7330f9e330684b809
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927830"
---
# <a name="how-to-resize-listobject-controls"></a>如何：調整 ListObject 控制項的大小
  在將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入 Microsoft Office Excel 活頁簿時，會設定該控制項的大小，不過也可以稍後再進行調整。 例如，您可能想要將兩個資料行的清單變更為三個資料行。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 您可以在文件層級專案中，於設計階段或執行階段調整 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項大小。 您可以 <xref:Microsoft.Office.Tools.Excel.ListObject> 在 VSTO 增益集專案中，于執行時間調整控制項的大小。

 本主題說明下列工作：

- [在設計階段調整 ListObject 控制項的大小](#designtime)

- [在檔層級專案中，于執行時間調整 ListObject 控制項的大小](#runtimedoclevel)

- [在 VSTO 增益集專案中，于執行時間調整 ListObject 控制項的大小](#runtimeaddin)

  如需控制項的詳細資訊 <xref:Microsoft.Office.Tools.Excel.ListObject> ，請參閱 [ListObject 控制項](../vsto/listobject-control.md)。

## <a name="resize-a-listobject-control-at-design-time"></a><a name="designtime"></a> 在設計階段調整 ListObject 控制項的大小
 若要調整清單的大小，您可以按一下並拖曳其中一個調整大小控點，或是在 [調整清單大小]  對話方塊中重新定義其大小。

### <a name="to-resize-a-list-by-using-the-resize-list-dialog-box"></a>使用 [調整清單大小] 對話方塊調整清單的大小

1. 按一下資料表中的任何位置  <xref:Microsoft.Office.Tools.Excel.ListObject> 。 功能區中的 [**資料表工具**  >  **設計**] 索引標籤隨即出現。

2. 在 [屬性] 區段中，按一下 [重 **設大小資料表**]。

    ![VSTO_ResizeTable](../vsto/media/vsto-resizetable.png)

3. 選取資料表的新資料範圍。

4. 按一下 [確定]  。

## <a name="resize-a-listobject-control-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> 在檔層級專案中，于執行時間調整 ListObject 控制項的大小
 您可以使用 <xref:Microsoft.Office.Tools.Excel.ListObject> 方法在執行階段調整 <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A> 控制項的大小。 您無法使用此方法將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項移至工作表上的新位置。 標頭必須留在相同的資料列，且已調整大小的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項必須與原始的清單物件重疊。 已調整大小的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項必須包含標頭資料列，和至少一個資料列。

### <a name="to-resize-a-list-object-programmatically"></a>以程式設計方式調整清單物件的大小

1. 在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上建立跨越資料格 **A1** 到 **B3** 的 `Sheet1`。

     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#6)]

2. 將清單大小調整成包含儲存格 **A1** 到 **C5**。

     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#7)]

## <a name="resize-a-listobject-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> 在 VSTO 增益集專案中，于執行時間調整 ListObject 的大小
 您可以在執行階段調整任何開啟之工作表上 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項的大小。 如需如何 <xref:Microsoft.Office.Tools.Excel.ListObject> 使用 VSTO 增益集將控制項加入工作表的詳細資訊，請參閱 [如何：將 ListObject 控制項加入工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)。

### <a name="to-resize-a-list-object-programmatically"></a>以程式設計方式調整清單物件的大小

1. 在 <xref:Microsoft.Office.Tools.Excel.ListObject> 上建立跨越資料格 **A1** 到 **B3** 的 `Sheet1`。

     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#12)]

2. 將清單大小調整成包含儲存格 **A1** 到 **C5**。

     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#13)]

## <a name="see-also"></a>另請參閱
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject 控制項](../vsto/listobject-control.md)
- [如何：將 ListObject 控制項加入至工作表](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [如何：調整書簽控制項的大小](../vsto/how-to-resize-bookmark-controls.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
