---
title: "如何： 從資料庫的資料填入工作表 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3b7cfb842a0372d4410a0794ff8ade901af713b1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>如何：將資料庫的資料填入工作表
  您可以在相同的方式，存取 Windows Form 專案中的資料存取文件層級 Office 專案中的資料。 您可以使用相同的工具和程式碼將資料帶入方案中，甚至可以使用 Windows Forms 控制項顯示資料。 此外，您也可以利用呼叫控制項，這是 Microsoft Office Excel 中已使用事件和資料繫結功能強化的原生物件的控制項。 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 下列範例示範如何使用設計工具，在文件層級專案中加入資料繫結控制項。 如需如何在執行階段將資料繫結控制項加入應用程式層級專案中的範例，請參閱[逐步解說： 複雜資料繫結在 VSTO 增益集專案](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)。  
  
 ![影片連結](../vsto/media/playvideo.gif "影片連結")相關的影片示範，請參閱[如何執行 i： 傳送資料到 Excel 工作表嗎？](http://go.microsoft.com/fwlink/?LinkID=130277)，和[How Do i： 使用資料庫的資料在 Excel 中？](http://go.microsoft.com/fwlink/?LinkID=130287)。  
  
## <a name="adding-a-data-bound-control-to-a-worksheet-at-design-time"></a>在設計階段加入資料繫結控制項加入工作表  
  
#### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>若要在工作表的資料庫中的資料填入  
  
1.  在 Visual Studio 中，開啟 Excel 文件層級專案，在設計工具中開啟工作表。  
  
2.  開啟 [資料來源]  視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱[加入新連接](../data-tools/add-new-connections.md)。  
  
3.  將欄位或您要從資料表拖曳**資料來源**視窗加入工作表。  
  
 工作表上建立下列控制項的其中一個：  
  
-   如果您拖曳欄位，<xref:Microsoft.Office.Tools.Excel.NamedRange>工作表上建立控制項。 如需詳細資訊，請參閱[NamedRange 控制項](../vsto/namedrange-control.md)。  
  
-   如果您拖曳資料表，<xref:Microsoft.Office.Tools.Excel.ListObject>工作表上建立控制項。 如需詳細資訊，請參閱 [ListObject Control](../vsto/listobject-control.md)。  
  
 您可以加入不同的控制項選取資料表或欄位在**資料來源**視窗，然後從下拉式清單中選擇不同的控制項。  
  
## <a name="objects-in-the-project"></a>專案中的物件  
 除了控制項之外，下列與資料相關的物件會自動加入專案：  
  
-   封裝連接到資料庫之資料表的具類型資料集。 如需詳細資訊，請參閱[Visual Studio 中的資料集工具](/visualstudio/data-tools/dataset-tools-in-visual-studio)。  
  
-   將控制項連接至具類型資料集的 <xref:System.Windows.Forms.BindingSource>。 如需詳細資訊，請參閱 [BindingSource Component Overview](/dotnet/framework/winforms/controls/bindingsource-component-overview)。  
  
-   TableAdapter 的具類型資料集連接至資料庫。 如需詳細資訊，請參閱 [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。  
  
-   TableAdapterManager，用來協調資料集內若要啟用階層式更新的資料表配置器。 如需詳細資訊，請參閱[階層式更新](../data-tools/hierarchical-update.md)和[TableAdapterManager 參考](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)。  
  
 當您執行專案時，控制項會顯示資料來源中的第一筆記錄。 您可以使用 <xref:System.Windows.Forms.BindingSource>，讓使用者捲動資料列。  
  
#### <a name="to-scroll-through-the-records"></a>捲動資料列  
  
-   使用 <xref:System.Windows.Forms.BindingSource> 方法，如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 和 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>。  
  
 如需如何將更新傳送至具類型資料集和資料庫資訊，請參閱[How to： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [加入新的資料來源](/visualstudio/data-tools/add-new-data-sources)   
 [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [如何： 從物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何： 從資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何： 從服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [如何： 從主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [如何 i： 將資料傳送到 Excel 工作表](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [如何： 使用 Excel 中的資料庫資料？](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  