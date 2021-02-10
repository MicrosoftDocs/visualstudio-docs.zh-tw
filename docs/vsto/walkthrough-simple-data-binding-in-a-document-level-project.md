---
title: 逐步解說：檔層級專案中的簡單資料系結
description: 瞭解檔層級專案中資料系結的基本概念，以及 SQL Server 資料庫中的單一資料欄位系結至 Microsoft Excel 中的命名範圍。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31084703a581999a1f25bfc82db6c36d9e2cbf6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937403"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>逐步解說：檔層級專案中的簡單資料系結
  本逐步解說示範檔層級專案中資料系結的基本概念。 SQL Server 資料庫中的單一資料欄位會系結至 Microsoft Office Excel 中的已命名範圍。 本逐步解說也會示範如何加入控制項，讓您可以在資料表中的所有記錄之間進行滾動。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本逐步解說將說明下列工作：

- 建立 Excel 專案的資料來源。

- 將控制項加入工作表。

- 在資料庫記錄中進行滾動。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

- 從 SQL Server 資料庫讀取和寫入的許可權。

## <a name="create-a-new-project"></a>建立新專案
 在這個步驟中，您將建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 Visual Basic 或 c #，建立名稱為 **My Simple Data Binding** 的 Excel 活頁簿專案。 確定已選取 [ **建立新檔** ]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

   Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的簡單資料** 系結] 專案加入 **方案總管**。

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

8. 選取 [ **Customers** ] 資料表旁的核取方塊。

9. 按一下 [完成] 。

   Wizard 會將 **Customers** 資料表加入至 [ **資料來源** ] 視窗。 它也會將具類型的資料集加入至 **方案總管** 中可見的專案。

## <a name="add-controls-to-the-worksheet"></a>將控制項新增至工作表
 針對這個逐步解說，您需要在第一個工作表上有兩個命名範圍和四個按鈕。 首先，從 [ **資料來源** ] 視窗加入兩個命名範圍，讓它們自動系結至資料來源。 接下來，從 [ **工具箱**] 加入按鈕。

### <a name="to-add-two-named-ranges"></a>加入兩個命名範圍

1. 確認 [ *我的簡單資料 Binding.xlsx* 活頁簿] 已在 Visual Studio 設計工具中開啟，並顯示 **Sheet1** 。

2. 開啟 [ **資料來源** ] 視窗，並展開 [ **Customers** ] 節點。

3. 選取 [ **公司名稱** ] 資料行，然後按一下出現的下拉箭號。

4. 在下拉式清單中選取 [ **NamedRange** ]，然後將 [ **公司名稱** ] 資料行拖曳至儲存格 **A1**。

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `companyNameNamedRange` 在儲存格 **A1** 中會建立名為的控制項。 同時， <xref:System.Windows.Forms.BindingSource> 已命名的 `customersBindingSource` 、資料表介面卡和 <xref:System.Data.DataSet> 實例會加入至專案。 控制項系結至 <xref:System.Windows.Forms.BindingSource> ，後者接著會系結至 <xref:System.Data.DataSet> 實例。

5. 在 [**資料來源**] 視窗中選取 [ **CustomerID** ] 資料行，然後按一下出現的下拉箭號。

6. 按一下下拉式清單中的 [ **NamedRange** ]，然後將 [ **CustomerID** ] 資料行拖曳至儲存格 **B1**。

7. 另一個名為的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項 `customerIDNamedRange` 是在資料格 **B1** 中建立，並系結至 <xref:System.Windows.Forms.BindingSource> 。

### <a name="to-add-four-buttons"></a>新增四個按鈕

1. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:System.Windows.Forms.Button> 控制項加入工作表的儲存格 **A3** 。

    此按鈕的名稱為 `Button1` 。

2. 依此順序將三個以上的按鈕新增至下列資料格，讓名稱如下所示：

   |資料格|(名稱)|
   |----------|--------------|
   |B3|Button2|
   |C3|Button3|
   |D3|Button4|

   下一步是要在按鈕中加入文字，並在 c # 中加入事件處理常式。

## <a name="initialize-the-controls"></a>初始化控制項
 設定按鈕文字並在事件期間新增事件處理常式 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 。

### <a name="to-initialize-the-controls"></a>若要初始化控制項

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **Sheet1** ] 或 [ **Sheet1.cs**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 將下列程式碼加入至 `Sheet1_Startup` 方法，以設定每個按鈕的文字。

    [!code-csharp[Trin_VstcoreDataExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#2)]
    [!code-vb[Trin_VstcoreDataExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#2)]

3. 針對 c #，請將按鈕 click 事件的事件處理常式加入至 `Sheet1_Startup` 方法。

    [!code-csharp[Trin_VstcoreDataExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#3)]

   現在，新增程式碼來處理 <xref:System.Windows.Forms.Control.Click> 按鈕的事件，讓使用者可以流覽記錄。

## <a name="add-code-to-enable-scrolling-through-the-records"></a>新增程式碼以啟用記錄的滾動
 將程式碼加入至 <xref:System.Windows.Forms.Control.Click> 每個按鈕的事件處理常式，以移動記錄。

### <a name="to-move-to-the-first-record"></a>移至第一個記錄

1. 新增按鈕事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button1` ，並加入下列程式碼以移至第一筆記錄：

     [!code-csharp[Trin_VstcoreDataExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#4)]

### <a name="to-move-to-the-previous-record"></a>移至上一個記錄

1. 新增按鈕事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button2` ，並加入下列程式碼，將位置向後移動一個：

     [!code-csharp[Trin_VstcoreDataExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#5)]

### <a name="to-move-to-the-next-record"></a>移到下一筆記錄

1. 新增按鈕事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button3` ，並加入下列程式碼以將位置前移一：

     [!code-csharp[Trin_VstcoreDataExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#6)]

### <a name="to-move-to-the-last-record"></a>移至最後一筆記錄

1. 新增按鈕事件的事件處理常式 <xref:System.Windows.Forms.Control.Click> `Button4` ，並加入下列程式碼以移至最後一筆記錄：

     [!code-csharp[Trin_VstcoreDataExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#7)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，以確定您可以流覽資料庫中的記錄。

### <a name="to-test-your-workbook"></a>測試您的活頁簿

1. 按 **F5** 執行您的專案。

2. 確認第一個記錄出現在 **A1** 和 **B1** 儲存格。

3. 按一下 [ **>** (`Button3`) ] 按鈕，並確認下一個記錄出現在儲存格 **A1** 和 **B1** 中。

4. 按一下 [其他] 滾動按鈕以確認記錄會如預期般變更。

## <a name="next-steps"></a>下一步
 本逐步解說會示範將命名範圍系結至資料庫中之欄位的基本概念。 接著可以執行下列一些工作：

- 快取資料，讓它可以離線使用。 如需詳細資訊，請參閱 [如何：快取資料供離線使用或在伺服器上使用](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)。

- 將資料格系結至資料表中的多個資料行，而不是一個欄位。 如需詳細資訊，請參閱 [逐步解說：檔層級專案中的複雜資料](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)系結。

- 使用 <xref:System.Windows.Forms.BindingNavigator> 控制項來流覽記錄。 如需詳細資訊，請參閱 [如何：使用 Windows Forms BindingNavigator 控制項來流覽資料](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms)。

## <a name="see-also"></a>另請參閱
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [逐步解說：檔層級專案中的複雜資料系結](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
