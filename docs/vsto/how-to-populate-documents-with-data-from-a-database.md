---
title: 如何： 的資料庫中的資料填入文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af068fc9cdacc0f681232ee4c7424d67d77f3a11
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756797"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>如何： 的資料庫中的資料填入文件

您可以用存取 Windows Form 專案資料的相同方式，存取 Microsoft Office 文件層級專案的資料。 使用相同的工具和程式碼，可從資料庫將資料帶入您的解決方案，而且可以使用 Windows Form 控制項顯示資料。

此外，也可以使用主控制項來顯示資料。 主控制項是 Microsoft Office Word 中的原生物件，已使用事件和資料繫結功能強化。 如需詳細資訊，請參閱 <<c0> [ 主項目和裝載控制項概觀](../vsto/host-items-and-host-controls-overview.md)。

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。 如需如何在 VSTO 增益集專案中新增資料繫結控制項，在執行階段的範例，請參閱 <<c0> [ 逐步解說： VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。

![影片連結](../vsto/media/playvideo.gif "影片連結")如需相關的影片示範，請參閱[資料繫結至 Word 2007 內容控制項使用 Visual Studio Tools for Office system (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785)。

## <a name="add-a-control-to-a-document-at-design-time"></a>在設計階段將控制項加入文件

### <a name="to-populate-a-document-with-data-from-a-database"></a>以資料庫的資料填入文件

1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中開啟 Word 文件層級專案，同時在設計工具中開啟文件。

2.  開啟**Zdroje dat**視窗，並從資料庫建立資料來源。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。

3.  將您想要的欄位拖曳**Zdroje dat**文件視窗。

內容控制項已加入文件。 內容控制項的類型取決於您選取的欄位資料類型。 如需詳細資訊，請參閱 <<c0> [ 內容控制項](../vsto/content-controls.md)。

您可以藉由選取中的資料欄位加入不同的控制項**Zdroje dat**視窗，然後從下拉式清單中選擇不同的控制項。

## <a name="objects-in-the-project"></a>專案中的物件

除了控制項之外，下列與資料相關的物件會自動加入專案：

-   封裝連接到資料庫之資料表的具類型資料集。 如需詳細資訊，請參閱 < [Visual Studio 中的資料集工具](../data-tools/dataset-tools-in-visual-studio.md)。

-   將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱 < [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)。

-   連接至資料庫的具類型資料集的 TableAdapter。 如需詳細資訊，請參閱 <<c0> [ 建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)。

-   TableAdapterManager，這用來協調資料集內若要啟用階層式更新的資料表配置器。 如需詳細資訊，請參閱 <<c0> [ 階層式更新](../data-tools/hierarchical-update.md)並[TableAdapterManager 參考](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。

當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。

### <a name="to-scroll-through-the-records"></a>捲動資料列

-   使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。

如需有關如何將更新傳送至具類型資料集和資料庫的資訊，請參閱 <<c0> [ 如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。

## <a name="see-also"></a>另請參閱

- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [新增資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何： 的物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [使用本機資料庫檔案，在 Office 方案概觀](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)