---
title: 如何：使用資料庫的資料填入檔
description: 瞭解如何在您的方案中使用資料庫中的資料，以及如何使用 Windows Forms 控制項來顯示檔中的資料。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0915d0ef57da5cba7fe73b6b374babe95b1a09c7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848075"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>如何：使用資料庫的資料填入檔

您可以用存取 Windows Form 專案資料的相同方式，存取 Microsoft Office 文件層級專案的資料。 使用相同的工具和程式碼，可從資料庫將資料帶入您的解決方案，而且可以使用 Windows Form 控制項顯示資料。

此外，也可以使用主控制項來顯示資料。 主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。 如需詳細資訊，請參閱 [主專案和主控制項總覽](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。 如需如何在執行時間于 VSTO 增益集專案中加入資料繫結控制項的範例，請參閱 [逐步解說： Vsto 增益集專案中的簡單資料](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)系結。

![影片連結](../vsto/media/playvideo.gif "視訊的連結") 如需相關的影片示範，請參閱 [使用 Office system 的 Visual Studio Tools 將資料系結至 Word 2007 內容控制項 (3.0) ](/previous-versions/office/developer/office-2007/bb967663(v=office.12))。

## <a name="add-a-control-to-a-document-at-design-time"></a>在設計階段將控制項加入檔

### <a name="to-populate-a-document-with-data-from-a-database"></a>以資料庫的資料填入文件

1. 在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟 Word 文件層級專案，同時在設計工具中開啟文件。

2. 開啟 [ **資料來源** ] 視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱 [加入新的連接](../data-tools/add-new-connections.md)。

3. 將您想要的欄位從 [ **資料來源** ] 視窗拖曳至您的檔。

內容控制項已加入文件。 內容控制項的類型取決於您選取的欄位資料類型。 如需詳細資訊，請參閱 [內容控制項](../vsto/content-controls.md)。

您可以在 [ **資料來源** ] 視窗中選取資料欄位，然後從下拉式清單中選擇不同的控制項，藉以加入不同的控制項。

## <a name="objects-in-the-project"></a>專案中的物件

除了控制項之外，下列與資料相關的物件會自動加入專案：

- 封裝連接到資料庫之資料表的具類型資料集。 如需詳細資訊，請參閱 [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

- 將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱 [BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)。

- 將具類型資料集連接至資料庫的 TableAdapter。 如需詳細資訊，請參閱 [建立和設定 tableadapter](../data-tools/create-and-configure-tableadapters.md)。

- TableAdapterManager，用來協調資料集中的資料表介面卡，以啟用階層式更新。 如需詳細資訊，請參閱 [階層式更新](../data-tools/hierarchical-update.md) 和 [TableAdapterManager 參考](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。

當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。

### <a name="to-scroll-through-the-records"></a>捲動資料列

- 使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。

如需有關如何將更新傳送至具類型資料集和資料庫的詳細資訊，請參閱 [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

## <a name="see-also"></a>另請參閱

- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新增新資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何：將物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [在 Office 方案中使用本機資料庫檔案總覽](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)