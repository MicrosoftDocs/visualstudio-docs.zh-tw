---
title: 逐步解說：建立使用快取的資料集的主版詳細資料關聯性
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3380b9c5302ed6e8a1bf6965f5fb1f259e3a6682
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438557"
---
# <a name="walkthrough-create-a-master-detail-relation-using-a-cached-dataset"></a>逐步解說：建立使用快取的資料集的主版詳細資料關聯性
  本逐步解說會示範在工作表，來建立主從式關聯和快取資料，以便可以離線使用方案。

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 在這個逐步解說期間，您將了解如何：

- 將控制項加入工作表。

- 設定快取的工作表中的資料集。

- 加入程式碼，以啟用捲動記錄。

- 測試您的專案。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。

- Northwind SQL Server 範例資料庫的存取。 資料庫可以是您的開發電腦或伺服器上。

- 讀取和寫入至 SQL Server 資料庫的權限。

## <a name="create-a-new-project"></a>建立新專案
 在此步驟中，您將建立的 Excel 活頁簿專案。

### <a name="to-create-a-new-project"></a>建立新的專案

1. 建立 Excel 活頁簿專案同名**我的主版詳細資料**，使用 Visual Basic 或 C#。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。

   Visual Studio 設計工具中開啟新的 Excel 活頁簿，並將**我的主版詳細資料**專案加入**方案總管 中**。

## <a name="create-the-data-source"></a>建立資料來源
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。

### <a name="to-create-the-data-source"></a>若要建立資料來源

1. 如果**資料來源**看不到視窗，顯示，請在功能表列選擇**檢視** > **其他 Windows**  >  **資料來源**。

2. 選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。

3. 選取 [**資料庫**，然後按一下**下一步]**。

4. 選取資料連接至 Northwind 範例 SQL Server 資料庫，或使用 [新增連線**新的連接**] 按鈕。

5. 選取或建立連線後, 按一下 [**下一步]**。

6. 清除 [可儲存連線，如果已選取，選項，然後按**下一步]**。

7. 依序展開**資料表**中的節點**資料庫物件**視窗。

8. 選取**訂單**資料表並**Order Details**資料表。

9. 按一下 [ **完成**]。

   精靈會新增兩個資料表**Zdroje dat**視窗。 它也將具類型資料集加入專案中可見**方案總管 中**。

## <a name="add-controls-to-the-worksheet"></a>將控制項加入工作表
 在此步驟中，您會將已命名的範圍、 list 物件和兩個按鈕新增至第一個工作表。 首先，新增已命名的範圍及清單中的物件**Zdroje dat**視窗，讓它們自動繫結至資料來源。 接下來，新增按鈕等，從**工具箱**。

### <a name="to-add-a-named-range-and-a-list-object"></a>將已命名的範圍和清單物件

1. 確認**我的主要 Detail.xlsx**活頁簿是在 Visual Studio 設計工具中開啟具有**Sheet1**顯示。

2. 開啟**資料來源**視窗中，展開**訂單**節點。

3. 選取  **OrderID**資料行，然後按一下出現的下拉式箭號。

4. 按一下  **NamedRange**在下拉式清單，然後拖曳**OrderID**加入儲存格的資料行**A2**。

     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`OrderIDNamedRange`會建立在資料格中**A2**。 在此同時<xref:System.Windows.Forms.BindingSource>名為`OrdersBindingSource`，資料表配接器和<xref:System.Data.DataSet>執行個體加入至專案。 控制項所繫結<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。

5. 向下捲動過去的資料行底下**訂單**資料表。 清單底部**訂單明細**資料表; 這裡是因為它的子系**訂單**資料表。 選取此選項**訂單明細**資料表，不是位於相同的層級**訂單**資料表，然後按一下出現的下拉式箭號。

6. 按一下  **ListObject**在下拉式清單，然後拖曳**OrderDetails**資料表以儲存格**A6**。

7. A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為**Order_DetailsListObject**建立在資料格中**A6**，並繫結至<xref:System.Windows.Forms.BindingSource>。

### <a name="to-add-two-buttons"></a>若要新增兩個按鈕

1. 從**通用控制項**索引標籤**工具箱**，加入<xref:System.Windows.Forms.Button>控制項加入儲存格**A3**工作表。

    此欄位稱為`Button1`。

2. 新增另一個<xref:System.Windows.Forms.Button>控制項加入儲存格**B3**工作表。

    此欄位稱為`Button2`。

   接下來，將標示要快取文件中的資料集。

## <a name="cache-the-dataset"></a>快取資料集
 將標示要由讓資料集，公開並設定快取文件中的資料集**CacheInDocument**屬性。

### <a name="to-cache-the-dataset"></a>快取資料集

1. 選取  **NorthwindDataSet**元件匣中。

2. 在 **屬性**視窗中，變更**修飾詞**屬性設**公用**。

    在啟用快取之前，必須是公用資料集。

3. 變更**CacheInDocument**屬性設 **，則為 True**。

   下一個步驟是將文字加入至按鈕，並在 C# 中，加入程式碼來連結事件處理常式。

## <a name="initialize-the-controls"></a>初始化的控制項
 設定按鈕文字，並新增事件處理常式期間<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件。

### <a name="to-initialize-the-data-and-the-controls"></a>若要初始化的資料和控制項

1. 在**方案總管 中**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs**，然後按一下**檢視程式碼**快顯功能表。

2. 將下列程式碼加入`Sheet1_Startup`方法來設定按鈕的文字。

     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]

3. 僅適用 C#，加入事件處理常式按鈕按一下事件`Sheet1_Startup`方法。

     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]

## <a name="add-code-to-enable-scrolling-through-the-records"></a>加入程式碼來啟用捲動記錄
 將程式碼加入<xref:System.Windows.Forms.Control.Click>記錄之間移動的每個按鈕事件處理常式。

### <a name="to-scroll-through-the-records"></a>捲動資料列

1. 新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button1`，並新增下列程式碼，向後移動記錄：

     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]

2. 新增事件處理常式<xref:System.Windows.Forms.Control.Click>事件的`Button2`，並新增下列程式碼，記錄中向前推進：

     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]

## <a name="test-the-application"></a>測試應用程式
 現在您可以測試您的活頁簿，確定資料會出現如預期般運作，而且您可以離線使用方案。

### <a name="to-test-the-data-caching"></a>若要測試資料的快取

1. 請按 **F5**。

2. 請確認已命名的範圍和清單物件會填入來自資料來源的資料。

3. 按一下按鈕，捲動瀏覽某些記錄。

4. 儲存活頁簿，然後關閉活頁簿和 Visual Studio。

5. 停用資料庫的連接。 拔除網路纜線從您的電腦，如果資料庫位於伺服器上，或如果資料庫是在您的開發電腦上停止 SQL Server 服務。

6. 開啟 Excel，然後再開啟**我的主要 Detail.xlsx**從*\bin*目錄 (*\My Master-Detail\bin*在 Visual Basic 或*\My Master-Detail\bin\偵錯*C# 中)。

7. 捲動以查看工作表運作正常中斷連線時記錄的一些問題。

8. 重新連接到資料庫。 將電腦連線到網路再如果資料庫位於伺服器上，或如果資料庫是在您的開發電腦上啟動 SQL Server 服務。

## <a name="next-steps"></a>後續步驟
 本逐步解說會示範在工作表上建立主版/詳細資料關聯性和快取資料集的基本概念。 接著可以執行下列一些工作：

- 部署方案。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>另請參閱
- [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)
- [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)
- [快取資料](../vsto/caching-data.md)
- [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)
