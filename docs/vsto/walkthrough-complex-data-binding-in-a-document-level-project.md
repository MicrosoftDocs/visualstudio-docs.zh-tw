---
title: 逐步解說：檔層級專案中的複雜資料系結
description: 瞭解如何將 Microsoft Excel 工作表中的多個資料格系結至 Northwind SQL Server 資料庫中的欄位。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2dc5708da09074c7d973336958c9e89c16bf9da6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927661"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>逐步解說：檔層級專案中的複雜資料系結
  本逐步解說示範檔層級專案中的複雜資料系結的基本概念。 您可以將 Microsoft Office Excel 工作表中的多個資料格系結至 Northwind SQL Server 資料庫中的欄位。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本逐步解說將說明下列工作：

- 將資料來源加入至您的活頁簿專案。

- 將資料繫結控制項加入至工作表。

- 將資料變更儲存回資料庫。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

- 從 SQL Server 資料庫讀取和寫入的許可權。

## <a name="create-a-new-project"></a>建立新專案
 第一個步驟是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立具有「 **我的複雜資料** 系結」名稱的 Excel 活頁簿專案。 在嚮導中，選取 [ **建立新檔**]。

     如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的複雜資料** 系結] 專案加入 **方案總管**。

## <a name="create-the-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [ **資料庫** ]，然後按 **[下一步]**。

4. 選取與 Northwind 範例 SQL Server 資料庫的資料連線，或使用 [ **新增連接** ] 按鈕來加入新的連接。

5. 選取或建立連接之後，請按 **[下一步]**。

6. 如果已選取連接，請清除選項來儲存連接，然後按 **[下一步]**。

7. 展開 [**資料庫物件**] 視窗中的 [**資料表**] 節點。

8. 選取 [ **員工** ] 資料表旁的核取方塊。

9. 按一下 [完成] 。

   Wizard 會將 **Employees** 資料表加入至 [ **資料來源** ] 視窗。 它也會將具類型的資料集加入至 **方案總管** 中可見的專案。

## <a name="add-controls-to-the-worksheet"></a>將控制項新增至工作表
 開啟活頁簿時，工作表會顯示 [ **員工** ] 資料表。 使用者可以對資料進行變更，然後按一下按鈕將這些變更儲存回資料庫。

 若要自動將工作表系結至資料表，您可以 <xref:Microsoft.Office.Tools.Excel.ListObject> 從 [ **資料來源** ] 視窗將控制項加入工作表。 若要授與使用者儲存變更的選項，請 <xref:System.Windows.Forms.Button> 從 [ **工具箱**] 新增控制項。

#### <a name="to-add-a-list-object"></a>若要加入清單物件

1. 確認 [ **我的複雜資料] Binding.xlsx** 活頁簿已在 Visual Studio 設計工具中開啟，並顯示 **Sheet1** 。

2. 開啟 [ **資料來源** ] 視窗，然後選取 [ **員工** ] 節點。

3. 按一下出現的下拉箭號。

4. 在下拉式清單中選取 [ **ListObject** ]。

5. 將 **Employees** 資料表拖曳至資料格 **A6**。

     <xref:Microsoft.Office.Tools.Excel.ListObject>名為的控制項 `EmployeesListObject` 會在資料格 **A6** 中建立。 同時， <xref:System.Windows.Forms.BindingSource> 已命名的 `EmployeesBindingSource` 、資料表介面卡和 <xref:System.Data.DataSet> 實例會加入至專案。 控制項系結至 <xref:System.Windows.Forms.BindingSource> ，後者接著會系結至 <xref:System.Data.DataSet> 實例。

### <a name="to-add-a-button"></a>若要加入按鈕

1. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入工作表的資料格 **A4** 。

   下一步是在工作表開啟時，將文字加入按鈕。

## <a name="initialize-the-control"></a>初始化控制項
 將文字加入至 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中的按鈕。

### <a name="to-initialize-the-control"></a>若要初始化控制項

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **Sheet1** ] 或 [ **Sheet1.cs**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼加入至 `Sheet1_Startup` 方法，以設定 b 的文字 `utton` 。

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. 針對 c #，請將事件的事件處理常式加入 <xref:System.Windows.Forms.Control.Click> 至 `Sheet1_Startup` 方法。

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   現在，新增程式碼來處理 <xref:System.Windows.Forms.Control.Click> 按鈕的事件。

## <a name="save-changes-to-the-database"></a>儲存資料庫的變更
 對資料所做的任何變更都只存在於本機資料集中，直到它們明確地儲存回資料庫為止。

### <a name="to-save-changes-to-the-database"></a>若要儲存資料庫的變更

1. 加入事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `button` ，並加入下列程式碼，將資料集內已進行的所有變更認可至資料庫。

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，確認資料如預期般出現，而且您可以動作清單物件中的資料。

### <a name="to-test-the-data-binding"></a>測試資料系結

- 按 **F5**。

     確認開啟活頁簿時，清單物件會填入 **employee 資料表中的資料** 。

### <a name="to-modify-data"></a>若要修改資料

1. 按一下 [ **資料格]**，其應包含名稱 **Davolio**。

2. 輸入名稱 **Anderson**，然後按 **enter**。

### <a name="to-modify-a-column-header"></a>若要修改資料行標題

1. 按一下包含資料行標題 **LastName** 的資料格。

2. 輸入 [ **姓氏**]，包括兩個單字之間的空格，然後按 **enter**。

### <a name="to-save-data"></a>若要儲存資料

1. 按一下工作表上的 [ **儲存** ]。

2. 結束 Excel。 當系統提示您儲存所做的變更時，請按一下 [ **否** ]。

3. 按 **F5** 再次執行專案。

     清單物件會填入 **Employees** 資料表中的資料。

4. 請注意，資料格 **B7** 中的名稱仍然是 **Anderson**，這是您所做的資料變更，並儲存回資料庫中。 因為資料行標頭未系結至資料庫，而且您未儲存對工作表所做的變更，所以資料行標題 **LastName** 已變更回其原始表單，而且沒有空格。

### <a name="to-add-new-rows"></a>若要加入新的資料列

1. 選取清單物件內的儲存格。

    新資料列會出現在清單底部，並 **\*** 在新資料列的第一個資料格中使用星號 () 。

2. 在空白資料列中加入下列資訊。

   |EmployeeID|姓氏|名字|標題|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|銷售經理|

### <a name="to-delete-rows"></a>刪除資料列

- 以滑鼠右鍵按一下工作表最左邊的數位 16 (資料列 16) ，然後按一下 [ **刪除**]。

### <a name="to-sort-the-rows-in-the-list"></a>若要排序清單中的資料列

1. 選取清單內的儲存格。

     箭號按鈕會出現在每個資料行標題中。

2. 按一下 [ **姓氏** ] 資料行標題中的箭號按鈕。

3. 按一下 [ **昇冪**]。

     資料列會依照姓氏的字母順序排序。

### <a name="to-filter-information"></a>篩選資訊

1. 選取清單內的儲存格。

2. 按一下 **標題** 欄標題中的箭號按鈕。

3. 按一下 [ **銷售代表**]。

     清單中只會顯示 [**標題**] 資料行中有 **銷售代表** 的資料列。

4. 再按一下 **標題** 欄標題中的箭號按鈕。

5. 按一下 [ **(所有)**。

     篩選會被移除，並顯示所有資料列。

## <a name="next-steps"></a>下一步
 本逐步解說說明將資料庫中的資料表系結至清單物件的基本概念。 接著可以執行下列一些工作：

- 快取資料，讓它可以離線使用。 如需詳細資訊，請參閱 [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

- 部署該方案。 如需詳細資訊，請參閱 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。

- 建立欄位和資料表之間的主要/詳細資料關聯。 如需詳細資訊，請參閱 [逐步解說：使用快取的資料集建立主要詳細資料關聯](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [逐步解說：檔層級專案中的簡單資料系結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
