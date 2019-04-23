---
title: 逐步解說：在文件層級專案中的複雜資料繫結
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aabd45871e55fd22b9b9e35597555fd13b15d6eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052528"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>逐步解說：在文件層級專案中的複雜資料繫結
  本逐步解說會示範在文件層級專案中的複雜資料繫結的基本概念。 您可以將 Microsoft Office Excel 工作表中的多個資料格繫結至 Northwind SQL Server 資料庫中的欄位。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 加入您的活頁簿專案中的資料來源。

- 您可以將資料繫結控制項加入工作表。

- 資料將變更儲存回資料庫。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 伺服器的存取權與 Northwind SQL Server 範例資料庫。

- 讀取和寫入至 SQL Server 資料庫的權限。

## <a name="create-a-new-project"></a>建立新專案
 第一個步驟是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立 Excel 活頁簿專案同名**My 複雜資料繫結**。 在精靈中，選取**建立新的文件**。

     如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**My 複雜資料繫結**專案加入**方案總管 中**。

## <a name="create-the-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [**資料庫**，然後按一下**下一步]**。

4. 選取資料連接至 Northwind 範例 SQL Server 資料庫，或使用 [新增連線**新的連接**] 按鈕。

5. 已選取或建立連接之後，請按一下**下一步**。

6. 清除 [可儲存連線，如果已選取，選項，然後按**下一步]**。

7. 依序展開**資料表**中的節點**資料庫物件**視窗。

8. 選取此核取方塊旁**員工**資料表。

9. 按一下 [ **完成**]。

   精靈會新增**員工**資料表**Zdroje dat**視窗。 它也將具類型資料集加入專案中可見**方案總管 中**。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 工作表會顯示**員工**資料表開啟活頁簿時。 使用者將能夠對資料進行變更，並按一下按鈕，然後將這些變更儲存回資料庫。

 若要自動將工作表連結到資料表，您可以加入<xref:Microsoft.Office.Tools.Excel.ListObject>控制項加入工作表，從**Zdroje dat**視窗。 若要讓使用者選擇儲存變更，新增<xref:System.Windows.Forms.Button>控制項從**工具箱**。

#### <a name="to-add-a-list-object"></a>若要加入清單物件

1. 確認**我的複雜資料 Binding.xlsx**活頁簿是在 Visual Studio 設計工具中開啟具有**Sheet1**顯示。

2. 開啟**資料來源**視窗，然後選取**員工**節點。

3. 按一下出現的下拉式箭號。

4. 選取  **ListObject**下拉式清單中。

5. 拖曳**員工**資料表來儲存格**A6**。

     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`EmployeesListObject`會建立在資料格中**A6**。 在此同時<xref:System.Windows.Forms.BindingSource>名為`EmployeesBindingSource`，資料表配接器和<xref:System.Data.DataSet>執行個體加入至專案。 控制項所繫結<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。

### <a name="to-add-a-button"></a>要加入按鈕

1. 從**通用控制項**索引標籤**工具箱**，加入<xref:System.Windows.Forms.Button>控制項加入儲存格**A4**工作表。

   下一個步驟是在工作表開啟時，將文字加入至按鈕。

## <a name="initialize-the-control"></a>初始化控制項
 將文字中的按鈕加入<xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>事件處理常式。

### <a name="to-initialize-the-control"></a>若要初始化的控制項

1. 在**方案總管 中**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs**，然後按一下**檢視程式碼**快顯功能表。

2. 將下列程式碼加入`Sheet1_Startup`方法，設定 b 的文字`utton`。

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. 僅適用 C#，加入事件處理常式<xref:System.Windows.Forms.Control.Click>事件，以`Sheet1_Startup`方法。

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   現在將新增程式碼來處理<xref:System.Windows.Forms.Control.Click>按鈕的事件。

## <a name="save-changes-to-the-database"></a>將變更儲存至資料庫
 任何已變更的資料只存在於本機的資料集之前明確儲存回資料庫。

### <a name="to-save-changes-to-the-database"></a>若要將變更儲存至資料庫

1. 新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`button`，並新增下列程式碼來確認已在資料集傳回至資料庫的所有變更。

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，來確認資料會出現如預期般運作，而且您可以操作的清單物件中的資料。

### <a name="to-test-the-data-binding"></a>若要測試的資料繫結

- 請按 **F5**。

     確認活頁簿開啟時，請使用資料填入清單物件**員工**資料表。

### <a name="to-modify-data"></a>若要修改資料

1. 按一下資料格**B7**，其中應包含名稱**Davolio**。

2. 輸入名稱**Anderson**，然後按**Enter**。

### <a name="to-modify-a-column-header"></a>若要修改的資料行標頭

1. 按一下包含資料行標頭儲存格**LastName**。

2. 型別**姓氏**，包括兩個單字，之間的空格，然後按**Enter**。

### <a name="to-save-data"></a>若要儲存資料

1. 按一下 **儲存**工作表上。

2. 結束 Excel。 按一下  **No**當系統提示您儲存您所做的變更。

3. 按下**F5**再次執行專案。

     清單物件會填入來自**員工**資料表。

4. 請注意，在儲存格的名稱**B7**仍**Anderson**，這是資料變更您進行，並儲存回資料庫。 資料行行首**LastName**變更回其原始形式，不含任何空格，因為具有資料行標頭未繫結到資料庫並沒有儲存您對工作表的變更。

### <a name="to-add-new-rows"></a>若要加入新的資料列

1. 選取資料格內的清單物件。

    新的資料列會出現在底部清單中，將以星號 (* *\\* * *) 新的資料列的第一個資料格中。

2. 新增下列資訊的空白資料列。

   |EmployeeID|LastName|FirstName|標題|
   |----------------|--------------|---------------|-----------|
   |10|Ito|Shu|銷售經理|

### <a name="to-delete-rows"></a>若要刪除資料列

- 16 （資料列 16） 上的最左側的工作表號碼，以滑鼠右鍵按一下，然後按一下**刪除**。

### <a name="to-sort-the-rows-in-the-list"></a>若要排序清單中的資料列

1. 選取清單內的資料格。

     箭號按鈕會出現在各個資料行標頭。

2. 按一下箭號按鈕，在**姓氏**資料行標頭。

3. 按一下 **遞增排序**。

     依姓氏依字母順序排序資料列。

### <a name="to-filter-information"></a>若要篩選資訊

1. 選取清單內的資料格。

2. 按一下箭號按鈕，在**Title**資料行標頭。

3. 按一下 **銷售代表**。

     此清單會顯示有這些資料列**業務代表**中**標題**資料行。

4. 按一下箭號按鈕，在**Title**資料行標頭一次。

5. 按一下  **（全部）**。

     會移除篩選，並顯示所有的資料列。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範在資料庫中的資料表繫結到清單物件的基本概念。 接著可以執行下列一些工作：

- 快取的資料，以便可以離線使用。 如需詳細資訊，請參閱[如何：離線或在伺服器上快取資料以用於](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

- 部署方案。 如需詳細資訊，請參閱 <<c0> [ 部署 Office 方案](../vsto/deploying-an-office-solution.md)。

- 建立主從式關聯欄位與資料表之間。 如需詳細資訊，請參閱[逐步解說：建立使用快取的資料集的主版詳細資料關聯性](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)。

## <a name="see-also"></a>另請參閱
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [逐步解說：在文件層級專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
