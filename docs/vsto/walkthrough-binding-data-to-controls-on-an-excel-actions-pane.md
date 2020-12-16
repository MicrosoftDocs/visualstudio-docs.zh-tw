---
title: 逐步解說：將資料系結至 Excel 執行窗格上的控制項
description: 將資料系結至 Microsoft Excel 中執行窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c53f4c1dfe9838fe4522dcc71b675a7f6b868d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524973"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>逐步解說：將資料系結至 Excel 執行窗格上的控制項
  本逐步解說示範如何將資料系結至 Microsoft Office Excel 中執行窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 本逐步解說將說明下列工作：

- 將控制項加入工作表。

- 建立執行窗格控制項。

- 將資料系結 Windows Forms 控制項加入至執行窗格控制項。

- 顯示應用程式開啟時的執行窗格。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [個人化 VISUAL STUDIO IDE](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

- 從 SQL Server 資料庫讀取和寫入的許可權。

## <a name="create-the-project"></a>建立專案
 第一步是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 使用 [ **我的 Excel 動作] 窗格** 的 [名稱] 建立 Excel 活頁簿專案。 在嚮導中，選取 [ **建立新檔**]。 如需詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [ **我的 Excel 動作] 窗格** 專案加入 **方案總管**。

## <a name="add-a-new-data-source-to-the-project"></a>將新的資料來源加入至專案

### <a name="to-add-a-new-data-source-to-the-project"></a>若要將新的資料來源加入至專案

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [**查看**  >  **其他 Windows**  >  **資料來源**]。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [ **資料庫** ]，然後按 **[下一步]**。

4. 選取與 Northwind 範例 SQL Server 資料庫的資料連線，或使用 [ **新增連接** ] 按鈕來加入新的連接。

5. 按 [下一步]  。

6. 如果已選取連接，請清除選項來儲存連接，然後按 **[下一步]**。

7. 展開 [**資料庫物件**] 視窗中的 [**資料表**] 節點。

8. 選取 [ **供應商** ] 資料表旁的核取方塊。

9. 展開 [ **Products** ] 資料表 **，然後選取**[ **ProductName**]、[已 **供應商**]、[ **QuantityPerUnit**] 和 [

10. 按一下 [完成] 。

    Wizard 將 [ **供應商** 資料表] 和 [ **產品** ] 資料表加入至 [ **資料來源** ] 視窗。 它也會將具類型的資料集加入至 **方案總管** 中可見的專案。

## <a name="add-controls-to-the-worksheet"></a>將控制項新增至工作表
 接下來，將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項和 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項新增至第一個工作表。

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>若要加入 NamedRange 控制項和 ListObject 控制項

1. 確認 [ **我的 Excel 動作] Pane.xlsx** 活頁簿已在 Visual Studio 設計工具中開啟，並 `Sheet1` 顯示。

2. 在 [ **資料來源** ] 視窗中，展開 [ **供應商** ] 資料表。

3. 按一下 [ **公司名稱** ] 節點上的下拉箭號，然後按一下 [ **NamedRange**]。

4. 將 [ **公司名稱** ] 從 [ **資料來源** ] 視窗拖曳至的儲存格 **A2** `Sheet1` 。

     隨即 <xref:Microsoft.Office.Tools.Excel.NamedRange> 建立名為的控制項 `CompanyNameNamedRange` ，且文字 \<CompanyName> 會出現在儲存格 **A2** 中。 同時， <xref:System.Windows.Forms.BindingSource> 已命名的 `suppliersBindingSource` 、資料表介面卡和 a <xref:System.Data.DataSet> 會加入至專案。 控制項系結至 <xref:System.Windows.Forms.BindingSource> ，後者接著會系結至 <xref:System.Data.DataSet> 實例。

5. 在 [ **資料來源** ] 視窗中，向下移動 [ **供應商** ] 資料表底下的資料行。 清單底部是 **Products** 資料表;這是因為它是 **供應商** 資料表的子系。 選取 [ **產品** ] 資料表，而不是與 [ **供應商** ] 資料表位於相同層級的資料表，然後按一下出現的下拉箭號。

6. 按一下下拉式清單中的 [ **ListObject** ]，然後將 [ **Products** ] 資料表拖曳至 **中的 [儲存格** ] `Sheet1` 。

     <xref:Microsoft.Office.Tools.Excel.ListObject>名為的控制項 `ProductNameListObject` 會在資料格 **A6** 中建立。 同時也 <xref:System.Windows.Forms.BindingSource> 會將名為 `productsBindingSource` 和資料表介面卡加入專案中。 控制項系結至 <xref:System.Windows.Forms.BindingSource> ，後者接著會系結至 <xref:System.Data.DataSet> 實例。

7. 針對 c #，請選取元件匣上的 [ **suppliersBindingSource** ]，然後在 [**屬性**] 視窗中將 [修飾詞 **] 屬性變更為 [** **內部**]。

## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格
 接下來，您需要具有下拉式方塊的執行窗格控制項。

### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項

1. 在 **方案總管** 中選取 [**我的 Excel 動作] 窗格** 專案。

2. 在 [專案] 功能表上，按一下 [加入新項目]。

3. 在 [ **加入新專案** ] 對話方塊中，選取 [ **動作] 窗格控制項**，將其命名為 **ActionsControl**，然後按一下 [ **加入**]。

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>若要將資料系結 Windows Forms 控制項加入至執行窗格控制項

1. 從 [**工具箱**] 的 [**通用控制項**] 索引標籤，將 <xref:System.Windows.Forms.ComboBox> 控制項拖曳至 [動作] 窗格控制項。

2. 將 **Size** 屬性變更為 **171，21**。

3. 調整使用者控制項的大小以符合下拉式方塊。

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>將 [動作] 窗格上的控制項系結至資料
 在本節中，您會將的資料來源設定 <xref:System.Windows.Forms.ComboBox> 為與 <xref:Microsoft.Office.Tools.Excel.NamedRange> 工作表上控制項相同的資料來源。

### <a name="to-set-data-binding-properties-of-the-control"></a>若要設定控制項的資料系結屬性

1. 在 [動作] 窗格控制項上按一下滑鼠右鍵，然後按一下 [ **視圖程式碼**]。

2. 將下列程式碼加入至執行 <xref:System.Windows.Forms.UserControl.Load> 窗格控制項的事件。

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. 在 c # 中，您必須建立的事件處理常式 `ActionsControl` 。 您可以將此程式碼放在函式中 `ActionsControl` 。 如需建立事件處理常式的詳細資訊，請參閱 [如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>顯示動作窗格
 在您于執行時間加入控制項之前，不會顯示 [動作] 窗格。

#### <a name="to-show-the-actions-pane"></a>顯示動作窗格

1. 在 **方案總管** 中，以滑鼠右鍵按一下 [ *ThisWorkbook* ] 或 [ *ThisWorkbook.cs*]，然後按一下 [ **視圖程式碼**]。

2. 在類別中建立使用者控制項的新實例 `ThisWorkbook` 。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. 在的 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> 事件處理常式中 `ThisWorkbook` ，將控制項加入至 [動作] 窗格。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的檔，以確認開啟檔時，[動作] 窗格會開啟，而且控制項具有主要/詳細資料關聯。

### <a name="to-test-your-document"></a>測試文件

1. 按 **F5** 執行您的專案。

2. 確認 [動作] 窗格是可見的。

3. 在清單方塊中選取公司。 確認公司名稱已列在 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項中，而且產品詳細資料列于 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項中。

4. 選取各種公司，以適當的方式確認公司名稱和產品詳細資料變更。

## <a name="next-steps"></a>後續步驟
 接著可以執行下列一些工作：

- 將資料系結至 Word 中的控制項。 如需詳細資訊，請參閱 [逐步解說：將資料系結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。

- 部署專案。 如需詳細資訊，請參閱 [使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：管理執行窗格的控制項版面配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
