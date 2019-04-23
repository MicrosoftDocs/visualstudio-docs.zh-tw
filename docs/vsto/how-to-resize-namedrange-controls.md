---
title: HOW TO：調整 NamedRange 控制項的大小
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ba5603fe759f55a85425bc61da0a470aa38d636c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099603"
---
# <a name="how-to-resize-namedrange-controls"></a>HOW TO：調整 NamedRange 控制項的大小
  您可以在將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入 Microsoft Office Excel 文件時，設定該控制項的大小，也可以稍後再進行調整。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 您可以在文件層級專案中，於設計階段或執行階段調整已命名範圍的大小。 您也可以在執行階段調整應用程式層級 VSTO 增益集中已命名範圍的大小。

 本主題說明下列工作：

- [在設計階段調整 NamedRange 控制項的大小](#designtime)

- [調整 NamedRange 控制項在文件層級專案中的執行階段的大小](#runtimedoclevel)

- [調整 NamedRange 控制項，在 VSTO 增益集專案中的執行階段的大小](#runtimeaddin)

## <a name="designtime"></a> 在設計階段調整 NamedRange 控制項的大小
 您可以在 [定義名稱]  對話方塊中重新定義已命名範圍的大小，以調整其大小。

### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>若要使用 [定義名稱] 對話方塊調整已命名範圍的大小

1. 以滑鼠右鍵按一下 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。

2. 按一下捷徑功能表上的 [管理已命名的範圍]  。

     [定義名稱]  對話方塊隨即出現。

3. 選取您要調整大小的已命名範圍。

4. 清除 [參考]  方塊。

5. 選取您要用於定義已命名範圍大小的儲存格。

6. 按一下 [確定] 。

## <a name="runtimedoclevel"></a> 調整 NamedRange 控制項在文件層級專案中的執行階段的大小
 您可以使用 <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 屬性，以程式設計方式調整已命名範圍的大小。

> [!NOTE]
>  在 [屬性]  視窗中， <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> 屬性標記為唯讀。

### <a name="to-resize-a-named-range-programmatically"></a>若要以程式的方式調整已命名範圍的大小

1. 在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的儲存格 [A1]  上建立 `Sheet1`控制項。

     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]

2. 調整已命名範圍的大小，以包含儲存格 [B1] 。

     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]

## <a name="runtimeaddin"></a> 調整 NamedRange 控制項，在 VSTO 增益集專案中的執行階段的大小
 您可以調整大小<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項上任何開啟的工作表，在執行階段。 如需有關如何新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項加入工作表使用 VSTO 增益集，請參閱[How to:將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。

### <a name="to-resize-a-named-range-programmatically"></a>若要以程式的方式調整已命名範圍的大小

1. 在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 的儲存格 [A1]  上建立 `Sheet1`控制項。

     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]

2. 調整已命名範圍的大小，以包含儲存格 [B1] 。

     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]

## <a name="see-also"></a>另請參閱
- [擴充 Word 文件和 Excel 活頁簿，VSTO 增益集在執行階段](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [將控制項加入 Office 文件，在執行階段](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Office 文件上的控制項](../vsto/controls-on-office-documents.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
- [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [NamedRange 控制項](../vsto/namedrange-control.md)
- [如何：將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [如何：調整書籤控制項的大小](../vsto/how-to-resize-bookmark-controls.md)
- [如何：調整 ListObject 控制項的大小](../vsto/how-to-resize-listobject-controls.md)
