---
title: 逐步解說：將資料繫結至 Excel 執行窗格上的控制項
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
ms.openlocfilehash: de51ead9b3395df1c48f1340e27bd8c891a87fa4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56647003"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>逐步解說：將資料繫結至 Excel 執行窗格上的控制項
  本逐步解說示範資料繫結至 Microsoft Office Excel 中的 [動作] 窗格上的控制項。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 這個逐步解說將說明下列工作：

-   將控制項加入工作表。

-   建立執行窗格控制項。

-   將資料繫結 Windows Form 控制項加入執行窗格控制項。

-   當應用程式開啟時，請顯示 [動作] 窗格。

> [!NOTE]
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

-   伺服器的存取權與 Northwind SQL Server 範例資料庫。

-   讀取和寫入至 SQL Server 資料庫的權限。

## <a name="create-the-project"></a>建立專案
 第一步是建立 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1.  建立 Excel 活頁簿專案同名**我的 Excel 執行窗格**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

     Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的 Excel 執行窗格**專案加入**方案總管 中**。

## <a name="add-a-new-data-source-to-the-project"></a>將新的資料來源新增至專案

### <a name="to-add-a-new-data-source-to-the-project"></a>將新的資料來源加入至專案

1. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [**資料庫**，然後按一下**下一步]**。

4. 選取資料連接至 Northwind 範例 SQL Server 資料庫，或使用 [新增連線**新的連接**] 按鈕。

5. 按 [ **下一步**]。

6. 清除 [可儲存連線，如果已選取，選項，然後按**下一步]**。

7. 依序展開**資料表**中的節點**資料庫物件**視窗。

8. 選取此核取方塊旁**供應商**資料表。

9. 依序展開**產品**資料表，然後選取**ProductName**， **SupplierID**， **QuantityPerUnit**，和**UnitPrice**.

10. 按一下 [ **完成**]。

    精靈會新增**供應商**資料表並**產品**資料表**Zdroje dat**視窗。 它也將具類型資料集加入專案中可見**方案總管 中**。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 接下來，新增<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項和<xref:Microsoft.Office.Tools.Excel.ListObject>第一個工作表的控制項。

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>若要將 NamedRange 控制項和 ListObject 控制項

1.  確認**我的 Excel 動作 Pane.xlsx**活頁簿是在 Visual Studio 設計工具中開啟與`Sheet1`顯示。

2.  在 [**資料來源**] 視窗中，展開**供應商**資料表。

3.  按一下下拉箭號**Company Name**節點，然後再按一下**NamedRange**。

4.  拖曳**Company Name**從**資料來源**加入儲存格的視窗**A2**在`Sheet1`。

     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`CompanyNameNamedRange`建立時，和文字\<公司名稱 > 資料格中**A2**。 在此同時<xref:System.Windows.Forms.BindingSource>名為`suppliersBindingSource`，資料表配接器和<xref:System.Data.DataSet>加入至專案。 控制項所繫結<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。

5.  在 [**資料來源**] 視窗中，向下捲動過去的資料行底下**供應商**資料表。 在清單底部**產品**資料表; 這裡是因為它的子系**供應商**資料表。 選取此選項**產品**資料表，不是位於相同的層級**供應商**資料表，然後按一下出現的下拉式箭號。

6.  按一下  **ListObject**在下拉式清單，將**產品**資料表以儲存格**A6**在`Sheet1`。

     A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為`ProductNameListObject`會建立在資料格中**A6**。 在此同時<xref:System.Windows.Forms.BindingSource>名為`productsBindingSource`和資料表配接器會新增至專案。 控制項所繫結<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。

7.  針對C#，因此請選取**suppliersBindingSource**元件匣中，以及變更**修飾詞**屬性設**內部**中**屬性**視窗。

## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格
 接下來，您需要執行窗格控制項有下拉式方塊。

### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項

1.  選取 [**我的 Excel 執行窗格**專案中**方案總管] 中**。

2.  在 [專案]  功能表中，按一下 [加入新項目] 。

3.  在**加入新項目**對話方塊中，選取**執行窗格控制項**，其命名**ActionsControl**，然後按一下**新增**。

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>若要將資料繫結 Windows Form 控制項加入執行窗格控制項

1.  從**通用控制項**索引標籤**工具箱**，拖曳<xref:System.Windows.Forms.ComboBox>執行窗格控制項的控制項。

2.  變更**大小**屬性設**171，21**。

3.  調整使用者控制項調整大小下拉式方塊的大小。

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>在 [動作] 窗格上的將控制項繫結至資料
 在本節中，您將設定的資料來源<xref:System.Windows.Forms.ComboBox>相同的資料來源以<xref:Microsoft.Office.Tools.Excel.NamedRange>工作表上的控制項。

### <a name="to-set-data-binding-properties-of-the-control"></a>若要設定控制項的資料繫結屬性

1.  以滑鼠右鍵按一下執行窗格控制項，然後按一下**檢視程式碼**。

2.  將下列程式碼加入<xref:System.Windows.Forms.UserControl.Load>執行窗格控制項的事件。

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3.  在C#，您必須建立的事件處理常式`ActionsControl`。 您可以將放在這段程式碼`ActionsControl`建構函式。 如需建立事件處理常式的詳細資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>顯示 [動作] 窗格
 [動作] 窗格看不到您在執行階段加入控制項之前。

#### <a name="to-show-the-actions-pane"></a>若要顯示 [動作] 窗格

1.  在 **方案總管 中**，以滑鼠右鍵按一下*ThisWorkbook.vb*或*ThisWorkbook.cs*，然後按一下 **檢視程式碼**。

2.  建立新的執行個體中的使用者控制項的`ThisWorkbook`類別。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3.  在 <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件處理常式`ThisWorkbook`，將控制項加入 動作 窗格。

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的文件，以確認動作 窗格中開啟文件開啟時，且控制項有主要/詳細資料關聯性。

### <a name="to-test-your-document"></a>測試文件

1.  按下**F5**執行您的專案。

2.  確認 [動作] 窗格已顯示。

3.  在清單方塊中選取一家公司。 確認公司名稱列在<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項和產品詳細資料，會列出在<xref:Microsoft.Office.Tools.Excel.ListObject>控制項。

4.  選取不同的公司，若要驗證的公司名稱和產品詳細資料會適當地變更。

## <a name="next-steps"></a>後續步驟
 接著可以執行下列一些工作：

-   將資料繫結至 Word 中的控制項。 如需詳細資訊，請參閱[逐步解說：將資料繫結至 Word 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)。

-   部署專案。 如需詳細資訊，請參閱 <<c0> [ 藉由使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。

## <a name="see-also"></a>另請參閱
- [執行窗格概觀](../vsto/actions-pane-overview.md)
- [如何：管理執行窗格控制項配置](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
