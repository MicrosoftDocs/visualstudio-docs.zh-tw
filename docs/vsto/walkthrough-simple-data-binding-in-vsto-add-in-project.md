---
title: 逐步解說： VSTO 增益集專案中的簡單資料系結
description: 瞭解如何在 Microsoft Word 檔中加入控制項，並在執行時間將控制項系結至資料。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- data binding [Office development in Visual Studio], Word
- data [Office development in Visual Studio], simple binding data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e1891173f10acfff74e0f7ef7ab17e29b258b80e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826833"
---
# <a name="walkthrough-simple-data-binding-in-vsto-add-in-project"></a>逐步解說： VSTO 增益集專案中的簡單資料系結

您可以將資料繫結至 VSTO 增益集專案中的主控制項和 Windows Form 控制項。 本逐步解說示範如何將控制項加入 Microsoft Office Word 文件，以及在執行階段將控制項繫結至資料。

[!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

本逐步解說將說明下列工作：

- 在設計階段將 <xref:Microsoft.Office.Tools.Word.ContentControl> 加入文件。

- 建立可將控制項連接到資料集執行個體的 <xref:System.Windows.Forms.BindingSource> 。

- 讓使用者能夠捲動記錄及在控制項中檢視它們。

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件

您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

- 已附加 `AdventureWorksLT` 範例資料庫之執行中 SQL Server 2005 或 SQL Server 2005 Express 執行個體的存取權。 您可以 `AdventureWorksLT` 從 [SQL Server 範例 GitHub](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)存放庫下載資料庫。 如需附加資料庫的詳細資訊，請參閱下列主題：

  - 若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱 [如何：附加資料庫 (SQL Server Management Studio) ](/sql/relational-databases/databases/attach-a-database)。

  - 若要使用命令列附加資料庫，請參閱 [如何：將資料庫檔案附加至 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-new-project"></a>建立新專案

第一步是建立 Word VSTO 增益集專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 Visual Basic 或 C#，建立名稱為 [ **從資料庫填入文件**] 的 Word VSTO 增益集專案。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會開啟 [ *ThisAddIn* ] 或 [ *ThisAddIn* ] 檔案，然後將 **從資料庫** 專案填入檔到 **方案總管**。

2. 如果您的專案是 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 以或為目標 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ，請將參考加入至 *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* 元件。 本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Forms 控制項加入文件。

## <a name="create-a-data-source"></a>建立資料來源

使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-add-a-typed-dataset-to-the-project"></a>將具類型資料集加入專案

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 按一下 [ **資料庫**]，然後按 [ **下一步**]。

4. 如果您有 `AdventureWorksLT` 資料庫的現有連接，請選擇這個連接，然後按 [ **下一步**]。

    否則，請按一下 [新增連接] ，然後使用 [加入連接]  對話方塊建立新的連接。 如需詳細資訊，請參閱 [加入新的連接](../data-tools/add-new-connections.md)。

5. 在 [將連接字串儲存到應用程式組態檔]  頁面上，按 [下一步] 。

6. 在 [ **選擇您的資料庫物件** ] 頁面中，展開 [ **資料表** ]，然後選取 [ **Customer (SalesLT)**]。

7. 按一下 [完成] 。

    *Adventureworksltdataset.xsd .xsd* 檔案會新增至 **方案總管**。 這個檔案會定義下列項目：

   - 具類型資料集，名稱為 `AdventureWorksLTDataSet`。 此資料集代表 AdventureWorksLT 資料庫中 **Customer (SalesLT)** 資料表的內容。

   - 名為的 TableAdapter `CustomerTableAdapter` 。 此 TableAdapter 可以用來讀取和寫入中的資料 `AdventureWorksLTDataSet` 。 如需詳細資訊，請參閱 [TableAdapter 總覽](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     您將在本逐步解說稍後用到這兩個物件。

## <a name="create-controls-and-binding-controls-to-data"></a>建立控制項並將控制項系結至資料

在本逐步解說中用來查看資料庫記錄的介面是基本的，而且會在檔內建立。 一個 <xref:Microsoft.Office.Tools.Word.ContentControl> 一次顯示單一資料庫記錄，而兩個 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項可讓您來回捲動記錄。 內容控制項使用 <xref:System.Windows.Forms.BindingSource> 連接到資料庫。

如需將控制項系結至資料的詳細資訊，請參閱將資料系結至 [Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="to-create-the-interface-in-the-document"></a>在文件中建立介面

1. 在 `ThisAddIn` 類別中，宣告下列控制項來顯示和捲動 `Customer` 資料庫的 `AdventureWorksLTDataSet` 資料表。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet1":::

2. 在 `ThisAddIn_Startup` 方法中，加入下列程式碼來初始化資料集、在資料集填入來自 `AdventureWorksLTDataSet` 資料庫的資訊。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet2":::

3. 將下列程式碼新增至 `ThisAddIn_Startup` 方法。 這會產生可擴充文件的主項目。 如需詳細資訊，請參閱 [在 VSTO 增益集中，于執行時間擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet3":::

4. 在文件開頭定義數個範圍。 這些範圍會識別插入文字和放置控制項的位置。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet4":::

5. 將介面控制項加入先前定義的範圍。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet5":::

6. 使用 `AdventureWorksLTDataSet` 將內容控制項繫結至 <xref:System.Windows.Forms.BindingSource>。 C# 開發人員請加入 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項的兩個事件處理常式。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet6":::

7. 加入下列程式碼來瀏覽資料庫記錄。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindatabase/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddindatabase/ThisAddIn.cs" id="Snippet7":::

## <a name="test-the-add-in"></a>測試增益集

當您開啟 Word 時，內容控制項會顯示來自 `AdventureWorksLTDataSet` 資料集的資料。 按 [ **下一個** ] 和 [ **前一個** ] 按鈕，即可捲動資料庫記錄。

### <a name="to-test-the-vsto-add-in"></a>測試 VSTO 增益集

1. 按 **F5**。

     會建立名為 `customerContentControl` 的內容控制項並填入資料。 同時間，名為 `adventureWorksLTDataSet` 的資料集物件，和名為 <xref:System.Windows.Forms.BindingSource> 的 `customerBindingSource` 會加入專案。 <xref:Microsoft.Office.Tools.Word.ContentControl> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。

2. 按 [ **下一個** ] 和 [ **前一個** ] 按鈕，即可捲動資料庫記錄。

## <a name="see-also"></a>另請參閱

- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：使用資料庫中的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [如何：使用資料庫的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：將服務的資料填入檔](../vsto/how-to-populate-documents-with-data-from-services.md)
- [如何：將物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：在工作表中滾動資料庫記錄](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [逐步解說：檔層級專案中的簡單資料系結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [逐步解說：檔層級專案中的複雜資料系結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [在 Office 方案中使用本機資料庫檔案總覽](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [新增新資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [如何：將物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：使用主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [在 Office 方案中使用本機資料庫檔案總覽](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 元件總覽](/dotnet/framework/winforms/controls/bindingsource-component-overview)
