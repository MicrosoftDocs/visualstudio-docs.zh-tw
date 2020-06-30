---
title: 如何：將資料庫的資料填入工作表
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 1b594014b2564b5730c1895a007294ee66e07637
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520116"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>如何：將資料庫的資料填入工作表

您可以存取檔層級 Office 專案中的資料，方法與存取 Windows Forms 專案中的資料相同。 您可以使用相同的工具和程式碼將資料帶入方案中，甚至可以使用 Windows Forms 控制項顯示資料。 此外，您還可以利用稱為主控制項的控制項，這是 Microsoft Office Excel 中的原生物件，已透過事件和資料系結功能來增強。 如需詳細資訊，請參閱[主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。 如需如何在執行時間于應用層級專案中加入資料繫結控制項的範例，請參閱[逐步解說： VSTO 增益集專案中的複雜資料](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)系結。

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>在設計階段將資料繫結控制項加入工作表

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>若要將資料庫中的資料填入工作表

1. 在 Visual Studio 中開啟 Excel 檔層級專案，並在設計工具中開啟工作表。

2. 開啟 [資料來源] **** 視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱[新增連接](../data-tools/add-new-connections.md)。

3. 將您想要的欄位或資料表從 [**資料來源**] 視窗拖曳至您的工作表。

工作表上會建立下列其中一個控制項：

- 如果您拖曳欄位， <xref:Microsoft.Office.Tools.Excel.NamedRange> 就會在工作表上建立控制項。 如需詳細資訊，請參閱[NamedRange control](../vsto/namedrange-control.md)。

- 如果您拖曳資料表， <xref:Microsoft.Office.Tools.Excel.ListObject> 就會在工作表上建立控制項。 如需詳細資訊，請參閱[ListObject control](../vsto/listobject-control.md)。

您可以在 [**資料來源**] 視窗中選取資料表或欄位，然後從下拉式清單中選擇不同的控制項，以加入不同的控制項。

## <a name="objects-in-the-project"></a>專案中的物件

除了控制項之外，下列與資料相關的物件會自動加入專案：

- 封裝連接到資料庫之資料表的具類型資料集。 如需詳細資訊，請參閱[Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

- 將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱[BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)。

- 將具類型資料集連接至資料庫的 TableAdapter。 如需詳細資訊，請參閱[TableAdapter 總覽](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

- TableAdapterManager，用來協調資料集中的資料表介面卡，以啟用階層式更新。 如需詳細資訊，請參閱[階層式更新](../data-tools/hierarchical-update.md)和[TableAdapterManager 參考](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。

當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。

### <a name="to-scroll-through-the-records"></a>捲動資料列

- 使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。

如需如何將更新傳送至具類型資料集和資料庫的詳細資訊，請參閱[如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

## <a name="see-also"></a>另請參閱

- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新增資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何：以物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：將資料庫中的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：將服務的資料填入檔](../vsto/how-to-populate-documents-with-data-from-services.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)