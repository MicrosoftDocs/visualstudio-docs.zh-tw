---
title: 逐步解說：VSTO 增益集專案中的複雜資料系結
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: efe99e4d12ea4ace6d6c996b816dc315c502fa47
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255557"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>逐步解說：VSTO 增益集專案中的複雜資料系結
  您可以將資料繫結至 VSTO 增益集專案中的主控制項和 Windows Forms 控制項。 本逐步解說示範如何在執行階段將控制項加入 Microsoft Office Excel 工作表，以及將控制項繫結至資料。

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 這個逐步解說將說明下列工作：

- 在執行階段將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項加入工作表。

- 建立將控制項連接至資料集的 <xref:System.Windows.Forms.BindingSource> 執行個體。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 已附加 `AdventureWorksLT` 範例資料庫之執行中 SQL Server 2005 或 SQL Server 2005 Express 執行個體的存取權。 您可以從`AdventureWorksLT` [CodePlex 網站](http://go.microsoft.com/fwlink/?LinkId=115611)下載資料庫。 如需附加資料庫的詳細資訊，請參閱下列主題：

  - 若要使用 SQL Server Management Studio 或 SQL Server Management Studio Express 附加資料庫，請參閱[如何：附加資料庫（SQL Server Management Studio）](/sql/relational-databases/databases/attach-a-database)。

  - 若要使用命令列附加資料庫，請參閱[如何：將資料庫檔案附加至 SQL Server Express](/previous-versions/sql/)。

## <a name="create-a-new-project"></a>建立新專案
 第一步是建立 Excel VSTO 增益集專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 Visual Basic 或 C#，建立名稱為「從資料庫填入工作表」的 Excel VSTO 增益集專案。

     如需詳細資訊，請參閱[如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

     Visual Studio 會開啟 `ThisAddIn.vb` 或 `ThisAddIn.cs` 檔案，然後將 [從資料庫填入工作表] 專案加入方案總管。

## <a name="create-a-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-add-a-typed-dataset-to-the-project"></a>將具類型資料集加入專案

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [**視圖** > ] [**其他視窗** > ] [**資料來源**]，以顯示。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 按一下 [ **資料庫**]，然後按 [ **下一步**]。

4. 如果您有 `AdventureWorksLT` 資料庫的現有連接，請選擇這個連接，然後按 [ **下一步**]。

    否則，請按一下 [ **新增連接**]，然後使用 [ **加入連接** ] 對話方塊建立新的連接。 如需詳細資訊，請參閱[新增連接](../data-tools/add-new-connections.md)。

5. 在 [將連接字串儲存到應用程式組態檔] 頁面上，按 [下一步]。

6. 在 [選擇您的資料庫物件] 頁面中，展開 [資料表] ，然後選取 [Address (SalesLT)]。

7. 按一下 [ **完成**]。

    *Adventureworksltdataset.xsd*會加入至**方案總管**。 這個檔案會定義下列項目：

   - 名為 `AdventureWorksLTDataSet`的具類型資料集。 這個資料集代表 AdventureWorksLT 資料庫中 [Address (SalesLT)] 資料表的內容。

   - 名為`AddressTableAdapter`的 TableAdapter。 這個 TableAdapter 可以用來讀取和寫入中的`AdventureWorksLTDataSet`資料。 如需詳細資訊，請參閱[TableAdapter 總覽](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)。

     您將在本逐步解說稍後用到這兩個物件。

## <a name="create-controls-and-bind-controls-to-data"></a>建立控制項並將控制項系結至資料
 在本逐步解說中，只要使用者開啟活頁簿， <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項便會顯示您選取的資料表中的所有資料。 清單物件使用 <xref:System.Windows.Forms.BindingSource> 將控制項連接到資料庫。

 如需將控制項系結至資料的詳細資訊，請參閱[將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>加入清單物件、資料集和資料表配接器

1. 在 `ThisAddIn` 類別中，宣告下列控制項來顯示 `Address` 資料集的 `AdventureWorksLTDataSet` 資料表。

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. 在 `ThisAddIn_Startup` 方法中，加入下列程式碼來初始化資料集，並在資料集中填入來自 `AdventureWorksLTDataSet` 資料集的資訊。

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. 將下列程式碼加入至 `ThisAddIn_Startup` 方法。 這會產生可擴充工作表的主項目。 如需詳細資訊，請參閱[在 VSTO 增益集的執行時間中擴充 Word 檔和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. 建立一個範圍並加入 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. 使用 `AdventureWorksLTDataSet` 將清單物件繫結至 <xref:System.Windows.Forms.BindingSource>。 將您要繫結的資料行名稱傳入清單物件。

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>測試增益集
 當您開啟 Excel 時， <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項會顯示 `Address` 資料集之 `AdventureWorksLTDataSet` 資料表中的資料。

### <a name="to-test-the-vsto-add-in"></a>測試 VSTO 增益集

- 請按 **F5**。

     工作表中會建立名為 <xref:Microsoft.Office.Tools.Excel.ListObject> 的 `addressListObject` 控制項。 同時也會將名為 `adventureWorksLTDataSet` 的資料集物件和名為 <xref:System.Windows.Forms.BindingSource> 的 `addressBindingSource` 加入專案。 <xref:Microsoft.Office.Tools.Excel.ListObject> 已繫結至 <xref:System.Windows.Forms.BindingSource>，而後者又繫結至資料集物件。

## <a name="see-also"></a>另請參閱

- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [如何：將資料庫中的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [如何：以資料庫中的資料填入檔](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [如何：使用服務中的資料填入檔](../vsto/how-to-populate-documents-with-data-from-services.md)
- [如何：以物件的資料填入檔](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [如何：在工作表中流覽資料庫記錄](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [如何：以主控制項的資料更新資料來源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [逐步解說：檔層級專案中的簡單資料系結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [逐步解說：檔層級專案中的複雜資料系結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [在 Office 方案中使用本機資料庫檔案總覽](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [新增資料來源](../data-tools/add-new-data-sources.md)
- [將 Windows Forms 控制項繫結至 Visual Studio 中的資料](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [在 Office 方案中使用本機資料庫檔案總覽](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 元件概觀](/dotnet/framework/winforms/controls/bindingsource-component-overview)
