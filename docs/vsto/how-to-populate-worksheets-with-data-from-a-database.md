---
title: HOW TO：從資料庫的資料填入工作表
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67c12843d00bf8d5af51fa7af3175077527afa58
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079135"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>HOW TO：從資料庫的資料填入工作表

您可以存取文件層級 Office 專案中的資料，您存取 Windows Form 專案中的資料的方式相同。 您可以使用相同的工具和程式碼將資料帶入方案中，甚至可以使用 Windows Forms 控制項顯示資料。 此外，您也可以利用稱為 「 主控制項，這些原生 Microsoft Office Excel 中的物件都已經過加強，與事件及資料繫結功能的控制項。 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。 如需如何在執行階段應用程式層級專案中加入資料繫結控制項的範例，請參閱[逐步解說：在 VSTO 增益集專案中的複雜資料繫結](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)。

![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[How do i:資料傳送到 Excel 工作表嗎？](http://go.microsoft.com/fwlink/?LinkID=130277)，和[How do i:使用 Excel 中的資料庫資料？](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>在設計階段將資料繫結控制項加入工作表

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>若要填入資料庫中的資料在工作表

1. 在設計工具中開啟工作表，在 Visual Studio 中，開啟 Excel 文件層級專案。

2. 開啟 [資料來源]  視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。

3. 將欄位或您想從資料表拖曳**Zdroje dat**視窗加入工作表。

工作表上建立下列控制項的其中一個：

- 如果您拖曳欄位，<xref:Microsoft.Office.Tools.Excel.NamedRange>工作表上建立控制項。 如需詳細資訊，請參閱 < [NamedRange 控制項](../vsto/namedrange-control.md)。

- 如果您拖曳資料表，<xref:Microsoft.Office.Tools.Excel.ListObject>工作表上建立控制項。 如需詳細資訊，請參閱 < [ListObject 控制項](../vsto/listobject-control.md)。

您可以加入不同的控制項選取資料表或欄位**Zdroje dat**視窗，然後從下拉式清單中選擇不同的控制項。

## <a name="objects-in-the-project"></a>專案中的物件

除了控制項之外，下列與資料相關的物件會自動加入專案：

- 封裝連接到資料庫之資料表的具類型資料集。 如需詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

- 將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱 < [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)。

- 連接至資料庫的具類型資料集的 TableAdapter。 如需詳細資訊，請參閱 < [TableAdapter 概觀](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

- TableAdapterManager，這用來協調資料集內若要啟用階層式更新的資料表配置器。 如需詳細資訊，請參閱 <<c0> [ 階層式更新](../data-tools/hierarchical-update.md)並[TableAdapterManager 參考](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。

當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。

### <a name="to-scroll-through-the-records"></a>捲動資料列

- 使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。

如需有關如何將更新傳送至具類型資料集和資料庫的資訊，請參閱[How to:從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

## <a name="see-also"></a>另請參閱

- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新增資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何：物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：資料庫中的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：服務中的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)
- [如何：從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [How do i將資料傳送到 Excel 工作表](http://go.microsoft.com/fwlink/?LinkID=130277)
- [How do i使用 Excel 中的資料庫資料？](http://go.microsoft.com/fwlink/?LinkID=130287)