---
title: NamedRange 控制項
description: 瞭解 NamedRange 控制項是具有唯一名稱、公開事件及可系結至資料的範圍。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1881afb0dd718eec3815ab9de3becbeaf070f5d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528086"
---
# <a name="namedrange-control"></a>NamedRange 控制項
  <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項是具有唯一名稱、可公開事件及繫結至資料的範圍。 如需詳細資訊，請參閱 [Excel 物件模型總覽](../vsto/excel-object-model-overview.md)。

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>建立控制項
 您可以透過文件層級專案，在設計階段或執行階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入 Microsoft Office Excel 工作表。

 在 VSTO 增益集中，您可以在執行階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入工作表。 如需詳細資訊，請參閱 [如何：將 NamedRange 控制項加入工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)。

> [!NOTE]
> 根據預設，當工作表關閉時，動態建立的具名範圍不會保存為工作表中的主控制項。 如需詳細資訊，請參閱 [在執行時間將控制項加入 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)。

 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項只能包含特定工作表上的範圍。 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項不可以具有適用於所有工作表的相對名稱，也不可以包含在活頁簿中合併兩個 (含) 以上工作表的範圍 (3-D 範圍)。

## <a name="bind-data-to-the-control"></a>將資料系結至控制項
 具名範圍看起來相當適用於複雜資料繫結，因為它可以包含許多儲存格；不過，這樣的範圍只是儲存格的集合，而無法輕易地對應至資料集中的特定資料行 因此， <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項只支援簡單資料繫結。 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項可用於複雜資料繫結。 如需詳細資訊，請參閱 [ListObject 控制項](../vsto/listobject-control.md)。

 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項可使用 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性繫結至資料來源。 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的預設資料繫結屬性是 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>。

 如果透過任何機制將繫結資料集中的資料更新， <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項會反映那些變更。

## <a name="formatting"></a>格式化
 可套用至 <xref:Microsoft.Office.Interop.Excel.Range> 的格式，也可套用至 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。 這包括框線、字型、數位格式和樣式。

## <a name="rename-the-control"></a>重新命名控制項
 當您將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項從 [工具箱] 加入工作表時，Visual Studio 會自動產生該控制項的名稱。 您可以在 [屬性]  視窗中變更該名稱。

## <a name="events"></a>事件
 下列事件適用於 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項：

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>另請參閱
- [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)
- [Office 開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Office 檔上的控制項](../vsto/controls-on-office-documents.md)
- [在執行時間將控制項新增至 Office 檔](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [如何：將 NamedRange 控制項加入至工作表](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [主專案和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
