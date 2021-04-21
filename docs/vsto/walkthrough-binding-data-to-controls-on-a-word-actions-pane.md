---
title: 逐步解說：將資料系結至 Word 執行窗格上的控制項
description: 將資料系結至 Microsoft Word 執行窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d94891520695117c7a395f81feda81e52f909fe6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824493"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>逐步解說：將資料系結至 Word 執行窗格上的控制項
  本逐步解說示範如何將資料系結至 Word 執行窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 本逐步解說將說明下列工作：

- 使用系結至資料的 Windows Forms 控制項來建立執行窗格。

- 使用主版/詳細資料關聯性來顯示控制項中的資料。

- 當應用程式開啟時顯示 [動作] 窗格。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

- 從 SQL Server 資料庫讀取和寫入的許可權。

## <a name="create-the-project"></a>建立專案
 第一個步驟是建立 Windows 文件專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 [ **我的單字動作] 窗格** 建立 word 檔專案。 在嚮導中，選取 [ **建立新檔**]。

     如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Word 檔，並將 [ **我的文字動作] 窗格** 專案加入 **方案總管**。

## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格
 針對這個逐步解說，您需要包含資料系結 Windows Forms 控制項的執行窗格控制項。 將資料來源加入至專案，然後將控制項從 [ **資料來源** ] 視窗拖曳到 [動作] 窗格控制項。

### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項

1. 在 **方案總管** 中選取 [**我的 Word 動作] 窗格** 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，選取 [ **動作] 窗格控制項**，將其命名為 **ActionsControl**，然後按一下 [ **加入**]。

### <a name="to-add-a-data-source-to-the-project"></a>若要將資料來源加入至專案

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

   > [!NOTE]
   > 如果無法使用 [ **顯示資料來源** ]，請按一下 Word 檔，然後再檢查一次。

2. 按一下 [ **加入新資料來源** ] 啟動 [ **資料來源設定向導]**。

3. 選取 [ **資料庫** ]，然後按 **[下一步]**。

4. 選取與 Northwind 範例 SQL Server 資料庫的資料連線，或使用 [ **新增連接** ] 按鈕來加入新的連接。

5. 按一下 [下一步] 。

6. 如果已選取連接，請清除選項來儲存連接，然後按 **[下一步]**。

7. 展開 [**資料庫物件**] 視窗中的 [**資料表**] 節點。

8. 選取 [ **供應商** ] 和 [ **產品** ] 資料表旁的核取方塊。

9. 按一下 [完成] 。

   Wizard 將 [ **供應商** 資料表] 和 [ **產品** ] 資料表加入至 [ **資料來源** ] 視窗。 它也會將具類型的資料集加入至 **方案總管** 中可見的專案。

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>若要將資料系結 Windows Forms 控制項加入至執行窗格控制項

1. 在 [ **資料來源** ] 視窗中，展開 [ **供應商** ] 資料表。

2. 按一下 [ **公司名稱** ] 節點上的下拉箭號，然後選取 [ **ComboBox**]。

3. 從 [**資料來源**] 視窗中，將 [**公司名稱**] 拖曳至 [動作] 窗格控制項。

     <xref:System.Windows.Forms.ComboBox>控制項是在 [動作] 窗格控制項上建立的。 同時，會在元件匣 <xref:System.Windows.Forms.BindingSource> 中，將名為的 `SuppliersBindingSource` 、資料表介面卡和 a <xref:System.Data.DataSet> 加入至專案中。

4. `SuppliersBindingNavigator`在 **元件** 匣中選取，然後按 **Delete** 鍵。 您將不會 `SuppliersBindingNavigator` 在此逐步解說中使用。

    > [!NOTE]
    > 刪除 `SuppliersBindingNavigator` 並不會移除為它產生的所有程式碼。 您可以移除此程式碼。

5. 移動下拉式方塊，使其位於標籤底下，並將 **Size** 屬性變更為 **171，21**。

6. 在 [ **資料來源** ] 視窗中，展開 [ **Products** ] 資料表，也就是 [ **供應商** ] 資料表的子系。

7. 按一下 [ **ProductName** ] 節點上的下拉箭號，然後選取 [ **ListBox**]。

8. 將 [ **ProductName** ] 拖曳到 [動作] 窗格控制項。

     <xref:System.Windows.Forms.ListBox>控制項是在 [動作] 窗格控制項上建立的。 同時， <xref:System.Windows.Forms.BindingSource> 已命名的 `ProductBindingSource` 和資料表介面卡會加入元件匣中的專案。

9. 移動清單方塊，使其位於標籤底下，並將 **Size** 屬性變更為 **171，95**。

10. 將 <xref:System.Windows.Forms.Button> 從 [ **工具箱** ] 拖曳至 [執行] 窗格控制項，並將它放在清單方塊下方。

11. 以滑鼠右鍵按一下 <xref:System.Windows.Forms.Button> ，再按一下快捷方式功能表上的 [ **屬性** ]，然後變更下列屬性。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|**插入**|
    |**Text**|**插入**|

12. 調整使用者控制項的大小以符合控制項。

## <a name="set-up-the-data-source"></a>設定資料來源
 若要設定資料來源，請將程式碼加入至執行 <xref:System.Windows.Forms.UserControl.Load> 窗格控制項的事件，以將中的資料填滿控制項 <xref:System.Data.DataTable> ，並設定 <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> 每個控制項的和屬性。

### <a name="to-load-the-control-with-data"></a>載入具有資料的控制項

1. 在 <xref:System.Windows.Forms.UserControl.Load> 類別的事件處理常式中 `ActionsControl` ，加入下列程式碼。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. 在 c # 中，您必須將事件處理常式附加至 <xref:System.Windows.Forms.UserControl.Load> 事件。 在呼叫之後，您可以將此程式碼放在函式中 `ActionsControl` `InitializeComponent` 。 如需如何建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>若要設定控制項的資料系結屬性

1. 選取 `CompanyNameComboBox` 控制項。

2. 在 [ **屬性** ] 視窗中，按一下 [ **DataSource** ] 屬性右邊的按鈕，然後選取 [ **suppliersBindingSource**]。

3. 按一下 [ **DisplayMember** ] 屬性右邊的按鈕，然後選取 [ **公司名稱**]。

4. 展開 [系結 **] 屬性，** 按一下 [ **Text** ] 屬性右邊的按鈕，然後選取 [ **無**]。

5. 選取 `ProductNameListBox` 控制項。

6. 在 [ **屬性** ] 視窗中，按一下 [ **DataSource** ] 屬性右邊的按鈕，然後選取 [ **productsBindingSource**]。

7. 按一下 [ **DisplayMember** ] 屬性右邊的按鈕，然後選取 [ **ProductName**]。

8. 展開 [系結] 屬性，按一下 [ **SelectedValue** **] 屬性右邊** 的按鈕，然後選取 [**無**]。

## <a name="add-a-method-to-insert-data-into-a-table"></a>新增方法，以將資料插入資料表中
 下一項工作是從繫結控制項讀取資料，並在 Word 檔中填入資料表。 首先，建立設定資料表中標題格式的程式，然後新增 `AddData` 方法以建立 Word 資料表並設定其格式。

### <a name="to-format-the-table-headings"></a>格式化表格標題

1. 在 `ActionsControl` 類別中，建立用來格式化資料表標題的方法。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>若要建立資料表

1. 在 `ActionsControl` 類別中，撰寫將建立資料表的方法（如果不存在的話），並將 [執行] 窗格中的資料加入至資料表。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>將文字插入 Word 表格

1. 將下列程式碼加入至 <xref:System.Windows.Forms.Control.Click> [ **插入** ] 按鈕的事件處理常式。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. 在 c # 中，您必須為按鈕的事件建立事件處理常式 <xref:System.Windows.Forms.Control.Click> 。  您可以將此程式碼放在 <xref:System.Windows.Forms.UserControl.Load> 類別的事件處理常式中 `ActionsControl` 。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>顯示動作窗格
 加入控制項後，[執行] 窗格就會變成可見。

### <a name="to-show-the-actions-pane"></a>顯示動作窗格

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ **ThisDocument** ] 或 [ **ThisDocument**]，然後按一下快捷方式功能表上的 [ **視圖程式碼** ]。

2. 在類別的頂端建立控制項的新實例， `ThisDocument` 使其看起來類似下列範例。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. 將程式碼加入 <xref:Microsoft.Office.Tools.Word.Document.Startup> 事件處理常式， `ThisDocument` 使其看起來類似下列範例。

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的檔，以確認開啟檔時顯示的是 [動作] 窗格。 在 [動作] 窗格上的控制項中測試 master/detail 關聯性，並確定按一下 [ **插入** ] 按鈕時，資料會填入單字資料表中。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 確認 [動作] 窗格是可見的。

3. 選取下拉式方塊中的公司，並確認 [ **產品** ] 清單方塊中的專案有變更。

4. 選取產品，按一下 [動作] 窗格上的 [ **插入** ]，並確認已將產品詳細資料加入至 Word 中的資料表。

5. 插入不同公司的其他產品。

## <a name="next-steps"></a>下一步
 本逐步解說會示範將資料系結至 Word 執行窗格上控制項的基本概念。 接著可以執行下列一些工作：

- 在 Excel 中將資料系結至控制項。 如需詳細資訊，請參閱逐步解說：將資料系結 [至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。

- 部署專案。 如需詳細資訊，請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：將執行窗格加入 Word 檔或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
