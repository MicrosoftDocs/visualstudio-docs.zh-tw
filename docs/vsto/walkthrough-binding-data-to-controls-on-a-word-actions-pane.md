---
title: 逐步解說：將資料繫結至 Word 執行窗格上的控制項
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a113cbdffffb202a832ce145c4507bf5845ff52d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926446"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>逐步解說：將資料繫結至 Word 執行窗格上的控制項
  本逐步解說會示範在 Word 執行窗格上的控制項資料繫結。 這些控制項會顯示 SQL Server 資料庫中資料表之間的主要/詳細資料關聯。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立動作 窗格中，使用 Windows Forms 控制項繫結至資料。  
  
-   若要在控制項中顯示的資料使用主要/詳細資料關聯性。  
  
-   當應用程式開啟時，請顯示 [動作] 窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
-   伺服器的存取權與 Northwind SQL Server 範例資料庫。  
  
-   讀取和寫入至 SQL Server 資料庫的權限。  
  
## <a name="create-the-project"></a>建立專案  
 第一個步驟是建立 Windows 文件專案。  
  
### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立 Word 文件專案名稱**My Word 執行窗格**。 在精靈中，選取**建立新的文件**。  
  
     如需詳細資訊，請參閱[＜How to：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**My Word 執行窗格**專案加入**方案總管 中**。  
  
## <a name="add-controls-to-the-actions-pane"></a>將控制項新增至 [動作] 窗格  
 此逐步解說中，您需要執行窗格控制項，其中包含資料繫結 Windows Form 控制項。 加入專案中，加入資料來源，然後將控制項從**Zdroje dat**執行窗格控制項的視窗。  
  
### <a name="to-add-an-actions-pane-control"></a>若要加入執行窗格控制項  
  
1.  選取 [ **My Word 執行窗格**專案中**方案總管] 中**。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在**加入新項目**對話方塊中，選取**執行窗格控制項**，其命名為**ActionsControl**，然後按一下**新增**。  
  
### <a name="to-add-a-data-source-to-the-project"></a>將資料來源加入至專案  
  
1. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。  
  
   > [!NOTE]  
   >  如果**顯示資料來源**，按一下 Word 文件，然後再檢查一次。  
  
2. 按一下 **加入新的資料來源**來啟動**資料來源組態精靈**。  
  
3. 選取 [**資料庫**，然後按一下**下一步]**。  
  
4. 選取資料連接至 Northwind 範例 SQL Server 資料庫，或使用 [新增連線**新的連接**] 按鈕。  
  
5. 按 [ **下一步**]。  
  
6. 清除 [可儲存連線，如果已選取，選項，然後按**下一步]**。  
  
7. 依序展開**資料表**中的節點**資料庫物件**視窗。  
  
8. 選取此核取方塊旁**供應商**並**產品**資料表。  
  
9. 按一下 [ **完成**]。  
  
   精靈會新增**供應商**資料表並**產品**資料表**Zdroje dat**視窗。 它也將具類型資料集加入專案中可見**方案總管 中**。  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>若要將資料繫結 Windows Form 控制項加入執行窗格控制項  
  
1.  在 [**資料來源**] 視窗中，展開**供應商**資料表。  
  
2.  按一下下拉箭號**Company Name**節點，然後選取**ComboBox**。  
  
3.  拖曳**CompanyName**從**Zdroje dat**執行窗格控制項的視窗。  
  
     A<xref:System.Windows.Forms.ComboBox>會建立執行窗格控制項上的控制項。 在此同時<xref:System.Windows.Forms.BindingSource>名為`SuppliersBindingSource`，資料表配接器和<xref:System.Data.DataSet>加入元件匣中的專案。  
  
4.  選取 `SuppliersBindingNavigator`中**元件**紙匣，然後按**刪除**。 您不會使用`SuppliersBindingNavigator`在本逐步解說。  
  
    > [!NOTE]  
    >  正在刪除`SuppliersBindingNavigator`不會移除所有針對它所產生的程式碼。 您可以移除此程式碼。  
  
5.  移動下拉式方塊，讓您可在 標籤 和 變更**大小**屬性設**171，21**。  
  
6.  在 [**資料來源**] 視窗中，展開**產品**也就是資料表的子系**供應商**資料表。  
  
7.  按一下下拉箭號**ProductName**節點，然後選取**ListBox**。  
  
8.  拖曳**ProductName**至執行窗格控制項。  
  
     A<xref:System.Windows.Forms.ListBox>會建立執行窗格控制項上的控制項。 在此同時<xref:System.Windows.Forms.BindingSource>名為`ProductBindingSource`和資料表配接器會新增至元件匣中的專案。  
  
9. 移動清單方塊，讓您可在 標籤 和 變更**大小**屬性設**171，95**。  
  
10. 拖曳<xref:System.Windows.Forms.Button>從**工具箱**拖曳至 [動作] 窗格控制項，並將它放在清單方塊下方。  
  
11. 以滑鼠右鍵按一下<xref:System.Windows.Forms.Button>，按一下**屬性**的捷徑功能表上，並變更下列屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |**名稱**|**插入**|  
    |**Text**|**插入**|  
  
12. 調整使用者控制項，以容納控制項的大小。  
  
## <a name="set-up-the-data-source"></a>設定資料來源  
 若要設定資料來源，將程式碼加入<xref:System.Windows.Forms.UserControl.Load>事件的執行窗格控制項以資料填入控制項<xref:System.Data.DataTable>，並將<xref:System.Windows.Forms.Binding.DataSource%2A>和<xref:System.Windows.Forms.BindingSource.DataMember%2A>每個控制項的屬性。  
  
### <a name="to-load-the-control-with-data"></a>載入具有資料的控制項  
  
1.  在 <xref:System.Windows.Forms.UserControl.Load>事件處理常式`ActionsControl`類別中，新增下列程式碼。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  在 C# 中，您必須將附加事件處理常式來<xref:System.Windows.Forms.UserControl.Load>事件。 您可以將此程式碼中的放`ActionsControl`建構函式，在呼叫之後`InitializeComponent`。 如需如何建立事件處理常式的詳細資訊，請參閱[How to:建立 Office 專案中的事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
### <a name="to-set-data-binding-properties-of-the-controls"></a>若要設定控制項的資料繫結屬性  
  
1.  選取 `CompanyNameComboBox` 控制項。  
  
2.  在 [**屬性**] 視窗中，按一下右邊的按鈕**DataSource**屬性，然後選取**suppliersBindingSource**。  
  
3.  按一下右邊的按鈕**DisplayMember**屬性，然後選取**CompanyName**。  
  
4.  依序展開**DataBindings**  屬性中，按一下右邊的按鈕**文字**屬性，然後選取**None**。  
  
5.  選取 `ProductNameListBox` 控制項。  
  
6.  在 [**屬性**] 視窗中，按一下右邊的按鈕**DataSource**屬性，然後選取**productsBindingSource**。  
  
7.  按一下右邊的按鈕**DisplayMember**屬性，然後選取**ProductName**。  
  
8.  依序展開**DataBindings**  屬性中，按一下右邊的按鈕**SelectedValue**屬性，然後選取**None**。  
  
## <a name="add-a-method-to-insert-data-into-a-table"></a>新增方法以將資料插入資料表  
 下一個工作是讀取繫結控制項中的資料，並填入 Word 文件中的資料表。 首先，建立的程序格式化資料表中的標題，然後加入`AddData`方法來建立並設定 Word 表格的格式。  
  
### <a name="to-format-the-table-headings"></a>若要格式化資料表標題  
  
1.  在 `ActionsControl`類別中，建立方法以格式化表格的標題。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
### <a name="to-create-the-table"></a>若要建立資料表  
  
1.  在 `ActionsControl`類別中，撰寫一個方法，將會建立資料表，如果其中一個尚未不存在，然後從 動作 窗格中加入表格的資料。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
### <a name="to-insert-text-into-a-word-table"></a>若要將文字插入 Word 表格  
  
1.  將下列程式碼加入<xref:System.Windows.Forms.Control.Click>事件處理常式**插入** 按鈕。  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  在 C# 中，您必須建立的事件處理常式<xref:System.Windows.Forms.Control.Click>按鈕的事件。  您可以將此程式碼中的放<xref:System.Windows.Forms.UserControl.Load>事件處理常式`ActionsControl`類別。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="show-the-actions-pane"></a>顯示 [動作] 窗格  
 加入控制項後，[動作] 窗格隨即顯示。  
  
### <a name="to-show-the-actions-pane"></a>若要顯示 [動作] 窗格  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下**ThisDocument.vb**或**ThisDocument.cs**，然後按一下**檢視程式碼**快顯功能表。  
  
2.  在頂端建立控制項的新執行個體`ThisDocument`類別，使它看起來如下列範例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  將程式碼加入<xref:Microsoft.Office.Tools.Word.Document.Startup>事件處理常式`ThisDocument`使它看起來如下列範例所示。  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="test-the-application"></a>測試應用程式  
 現在您可以測試您的文件，確認文件開啟時，會出現 [動作] 窗格。 測試主要/詳細資料關聯性，在 [動作] 窗格上的控制項，並確定在 Word 中，填入資料的資料表**插入**按一下按鈕時。  
  
### <a name="to-test-your-document"></a>測試文件  
  
1.  按下**F5**執行您的專案。  
  
2.  確認 [動作] 窗格已顯示。  
  
3.  下拉式方塊中選取一家公司，並確認中的項目**產品**清單方塊中變更。  
  
4.  選取的產品，請按一下**插入**上 動作 窗格中，並確認 產品詳細資料會新增至 Word 中的資料表。  
  
5.  從各種公司中插入額外的產品。  
  
## <a name="next-steps"></a>後續步驟  
 本逐步解說示範資料繫結至 word 執行窗格上的控制項基本的概念。 接著可以執行下列一些工作：  
  
-   將資料繫結至 Excel 中的控制項。 如需詳細資訊，請參閱[逐步解說：將資料繫結至 Excel 執行窗格上的控制項](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)。  
  
-   部署專案。 如需詳細資訊，請參閱 <<c0> [ 藉由使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行窗格概觀](../vsto/actions-pane-overview.md)   
 [如何：執行窗格加入 Word 文件或 Excel 活頁簿](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
