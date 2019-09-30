---
title: 逐步解說：將資料系結至 Excel 執行窗格上的控制項
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
ms.openlocfilehash: 1543f872961d556674dd5ad6b3f5b8071d2d404b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253887"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>逐步解說：將資料系結至 Excel 執行窗格上的控制項
  本逐步解說示範如何將資料系結至 Microsoft Office Excel 中執行窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

- 將控制項加入至工作表。

- 建立執行窗格控制項。

- 將資料系結 Windows Forms 控制項加入至 [動作] 窗格控制項。

- 當應用程式開啟時顯示 [動作] 窗格。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- 具有 Northwind SQL Server 範例資料庫之伺服器的存取權。

- SQL Server 資料庫的讀取和寫入權限。

## <a name="create-the-project"></a>建立專案
 第一步是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立名為 [ **My Excel 動作] 窗格**的 Excel 活頁簿專案。 在嚮導中，選取 [**建立新檔**]。 如需詳細資訊，請參閱[如何：在 Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)中建立 Office 專案。

     Visual Studio 會在設計工具中開啟新的 Excel 活頁簿，並將 [**我的 Excel 動作] 窗格**專案加入**方案總管**。

## <a name="add-a-new-data-source-to-the-project"></a>將新的資料來源加入至專案

### <a name="to-add-a-new-data-source-to-the-project"></a>若要將新的資料來源加入至專案

1. 如果看不到 [**資料來源**] 視窗，請在功能表列上選擇 [**視圖** > ] [**其他視窗** > ] [**資料來源**]，以顯示。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [**資料庫**]，然後按 **[下一步]** 。

4. 選取 Northwind 範例 SQL Server 資料庫的資料連線，或使用 [**新增連接**] 按鈕來加入新的連接。

5. 按 [ **下一步**]。

6. 清除選項以儲存連線（如果已選取），然後按 **[下一步]** 。

7. 展開 [**資料庫物件**] 視窗中的 [**資料表**] 節點。

8. 選取 [**供應商**] 資料表旁的核取方塊。

9. 展開 [ **Products** ]**資料表，然後**選取 [ **ProductName**]、[已**QuantityPerUnit**] 和 [**單價**]。

10. 按一下 [ **完成**]。

    Wizard 會將 [**供應商**資料表和**產品**] 資料表加入至 [**資料來源**] 視窗。 它也會將具型別資料集加入至**方案總管**中可見的專案。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 接下來，將<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項<xref:Microsoft.Office.Tools.Excel.ListObject>和控制項加入至第一個工作表。

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>若要加入 NamedRange 控制項和 ListObject 控制項

1. 確認 [**我的 Excel 動作] 窗格 .xlsx**活頁簿已在 Visual Studio 設計工具中開啟`Sheet1` ，並顯示。

2. 在 [**資料來源**] 視窗中，展開 [**供應商**] 資料表。

3. 按一下 [**公司名稱**] 節點上的下拉箭號，然後按一下 [ **NamedRange**]。

4. 將 [**公司名稱**] 從 [**資料來源**] 視窗拖曳`Sheet1`至 [ **A2** ] 儲存格。

     隨即會`CompanyNameNamedRange`建立名為的<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，而且 [公司名稱]>會\<出現在 A2 儲存格中。 同時， <xref:System.Windows.Forms.BindingSource>名為`suppliersBindingSource`的<xref:System.Data.DataSet>資料表介面卡和會加入至專案。 控制項會系結至<xref:System.Windows.Forms.BindingSource>，而後者又會系結<xref:System.Data.DataSet>至實例。

5. 在 [**資料來源**] 視窗中，向下流覽 [**供應商**] 資料表底下的資料行。 清單底部是**Products**資料表;這是因為它是「**供應商**」資料表的子系。 選取 [此**產品**] 資料表，而不是與 [**供應商**] 資料表位於相同層級的資料表，然後按一下出現的下拉箭號。

6. 按一下下拉式清單中的 [ **ListObject** ]，然後將**Products**資料表拖曳至中`Sheet1`的儲存格**A6** 。

     會<xref:Microsoft.Office.Tools.Excel.ListObject>在單元`ProductNameListObject`格**A6**中建立名為的控制項。 同時， <xref:System.Windows.Forms.BindingSource>名為`productsBindingSource`和資料表介面卡的會加入至專案。 控制項會系結至<xref:System.Windows.Forms.BindingSource>，而後者又會系結<xref:System.Data.DataSet>至實例。

7. 僅C#針對，選取元件匣上的 [ **suppliersBindingSource** ]，然後**將 [修飾**詞] 屬性變更為 [**內部**] 的 [**屬性**] 視窗。

## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格
 接下來，您需要具有下拉式方塊的執行窗格控制項。

### <a name="to-add-an-actions-pane-control"></a>若要加入動作窗格控制項

1. 在**方案總管**中選取 [**我的 Excel 動作] 窗格**專案。

2. 在 [專案] 功能表中，按一下 [加入新項目]。

3. 在 [**加入新專案**] 對話方塊中，選取 [**動作] 窗格控制項**，將它命名為**ActionsControl**，然後按一下 [**新增**]。

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>若要將資料系結 Windows Forms 控制項加入至執行窗格控制項

1. 從 [**工具箱**] 的 [**通用控制項**] 索引卷<xref:System.Windows.Forms.ComboBox>標，將控制項拖曳至 [動作] 窗格控制項。

2. 將**Size**屬性變更為**171，21**。

3. 調整使用者控制項的大小，使其符合下拉式方塊。

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>將 [動作] 窗格上的控制項系結至資料
 在本節中，您會將的資料來源<xref:System.Windows.Forms.ComboBox>設定為與工作表上的<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項相同的資料來源。

### <a name="to-set-data-binding-properties-of-the-control"></a>設定控制項的資料系結屬性

1. 以滑鼠右鍵按一下 [動作] 窗格控制項，然後按一下 [**查看程式碼**]。

2. 將下列程式碼新增至<xref:System.Windows.Forms.UserControl.Load> [動作] 窗格控制項的事件。

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. 在C#中，您必須建立的`ActionsControl`事件處理常式。 您可以將此程式碼放`ActionsControl`在函式中。 如需建立事件處理常式的詳細資訊[，請參閱如何：在 Office 專案](../vsto/how-to-create-event-handlers-in-office-projects.md)中建立事件處理常式。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>顯示 [動作] 窗格
 在您于執行時間加入控制項之前，不會顯示 [動作] 窗格。

#### <a name="to-show-the-actions-pane"></a>顯示 [動作] 窗格

1. 在**方案總管**中，以滑鼠右鍵按一下 [ *ThisWorkbook* ] 或 [ *ThisWorkbook.cs*]，然後按一下 [ **View Code**]。

2. 在`ThisWorkbook`類別中建立使用者控制項的新實例。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. 在的`ThisWorkbook`事件處理常式中，將控制項加入 [動作] 窗格。 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的檔，確認在檔開啟時，[動作] 窗格會開啟，而且控制項具有主要/詳細資料關聯性。

### <a name="to-test-your-document"></a>測試文件

1. 按**F5**執行您的專案。

2. 確認 [動作] 窗格是可見的。

3. 在清單方塊中選取公司。 確認公司名稱列在<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項中，而且產品詳細資料列<xref:Microsoft.Office.Tools.Excel.ListObject>在控制項中。

4. 選取 [各種公司] 以確認公司名稱和產品詳細資料會適當地變更。

## <a name="next-steps"></a>後續步驟
 接著可以執行下列一些工作：

- 將資料系結至 Word 中的控制項。 如需詳細資訊，請參閱[逐步解說：將資料系結至 [Word 動作]](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)窗格上的控制項。

- 部署專案。 如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

## <a name="see-also"></a>另請參閱
- [動作窗格總覽](../vsto/actions-pane-overview.md)
- [如何：管理動作窗格上的控制項版面配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [將資料系結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
