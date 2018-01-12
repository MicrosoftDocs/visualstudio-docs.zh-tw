---
title: "逐步解說： 建立主版詳細資料的關聯性，使用快取的資料集 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- master-detail tables [Office development in Visual Studio], walkthroughs
- data caching [Office development in Visual Studio], Master/Detail Relation
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 161fdc5e35a24b1318a44d2102867961330ba559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-master-detail-relation-using-a-cached-dataset"></a>逐步解說： 建立主版詳細資料的關聯性，使用快取的資料集
  本逐步解說示範 」 的工作表上建立主從式關聯，以便可以離線使用方案快取資料。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 在這個逐步解說期間，您將了解如何：  
  
-   將控制項加入工作表。  
  
-   設定要快取的工作表中的資料集。  
  
-   加入程式碼，以啟用捲動記錄。  
  
-   測試您的專案。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置。 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
-   Northwind SQL Server 範例資料庫的存取。 資料庫可以在開發電腦或伺服器上。  
  
-   讀取和寫入至 SQL Server 資料庫的權限。  
  
## <a name="creating-a-new-project"></a>建立新專案  
 在此步驟中，您將建立的 Excel 活頁簿專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
1.  建立名稱的 Excel 活頁簿專案**我的主檔/明細**，使用 Visual Basic 或 C#。 請確定**建立新的文件**已選取。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
 Visual Studio 設計工具中開啟新 Excel 活頁簿，並將**我的主檔/明細**專案加入**方案總管 中**。  
  
## <a name="creating-the-data-source"></a>建立資料來源  
 使用 [ **資料來源** ] 視窗將型別資料集加入專案。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  如果看不到 [ **資料來源** ] 視窗，請在功能表列選擇 [ **檢視**]、[ **其他視窗**]、[ **資料來源**] 即可顯示。  
  
2.  選擇 [ **加入新資料來源** ] 以啟動 [ **資料來源組態精靈**]。  
  
3.  選取**資料庫**，然後按一下 **下一步**。  
  
4.  選取資料連接至 Northwind 範例 SQL Server 資料庫，或加入新的連接使用**新連線** 按鈕。  
  
5.  選取或建立連接之後, 按**下一步**。  
  
6.  如果已選取，儲存連接選項，然後按清除**下一步**。  
  
7.  展開**資料表**節點**資料庫物件**視窗。  
  
8.  選取**訂單**資料表和**Order Details**資料表。  
  
9. 按一下 [ **完成**]。  
  
 精靈會新增兩個資料表**資料來源**視窗。 它也會將具類型資料集加入至您的專案中可見的**方案總管 中**。  
  
## <a name="adding-controls-to-the-worksheet"></a>將控制項加入工作表  
 在此步驟中，您將會加入具名的範圍、 清單物件，以及兩個按鈕第一個工作表。 首先，新增的已命名的範圍和清單物件從**資料來源**視窗，讓它們自動繫結至資料來源。 接下來，加入按鈕等，從**工具箱**。  
  
#### <a name="to-add-a-named-range-and-a-list-object"></a>若要加入的具名的範圍和清單物件  
  
1.  確認**我的主要 Detail.xlsx**活頁簿是在 Visual Studio 設計工具中開啟與**Sheet1**顯示。  
  
2.  開啟**資料來源**視窗中，展開 **訂單**節點。  
  
3.  選取**OrderID**資料行，然後按一下出現的下拉式箭號。  
  
4.  按一下**NamedRange**下拉式清單中，然後拖曳**OrderID**儲存格的資料行**A2**。  
  
     A<xref:Microsoft.Office.Tools.Excel.NamedRange>控制項，名為`OrderIDNamedRange`建立在資料格中**A2**。 同時，<xref:System.Windows.Forms.BindingSource>名為`OrdersBindingSource`，資料表配接器和<xref:System.Data.DataSet>執行個體加入至專案。 控制項繫結至<xref:System.Windows.Forms.BindingSource>，它接著會繫結至<xref:System.Data.DataSet>執行個體。  
  
5.  向下捲動，超過的資料行下**訂單**資料表。 在清單底部**Order Details**資料表; 這裡是因為它的子系**訂單**資料表。 選取此選項**Order Details**資料表，不是位於相同的層級**訂單**資料表，然後會出現下拉箭號。  
  
6.  按一下**ListObject**下拉式清單中，然後拖曳**OrderDetails**表格儲存格**A6**。  
  
7.  A<xref:Microsoft.Office.Tools.Excel.ListObject>控制項，名為**Order_DetailsListObject**建立在資料格中**A6**，而且繫結至<xref:System.Windows.Forms.BindingSource>。  
  
#### <a name="to-add-two-buttons"></a>若要加入兩個按鈕  
  
1.  從**通用控制項** 索引標籤**工具箱**，新增<xref:System.Windows.Forms.Button>控制項加入儲存格**A3**工作表。  
  
     這個按鈕名為`Button1`。  
  
2.  加入另一個<xref:System.Windows.Forms.Button>控制項加入儲存格**B3**工作表。  
  
     這個按鈕名為`Button2`。  
  
 接下來，將標示要快取文件中的資料集。  
  
## <a name="caching-the-dataset"></a>快取資料集  
 將標示要藉由公用和設定資料集快取文件中的資料集**CacheInDocument**屬性。  
  
#### <a name="to-cache-the-dataset"></a>快取資料集  
  
1.  選取**NorthwindDataSet**在元件匣中。  
  
2.  在**屬性**視窗中，變更**修飾詞**屬性**公用**。  
  
     之前已啟用快取資料集必須是公用的。  
  
3.  變更**CacheInDocument**屬性**True**。  
  
 下一個步驟是將文字加入至按鈕，並在 C# 中，加入程式碼來攔截 (hook) 事件處理常式。  
  
## <a name="initializing-the-controls"></a>初始化控制項  
 設定按鈕文字和新增事件處理常式期間<xref:Microsoft.Office.Tools.Excel.Workbook.Startup>事件。  
  
#### <a name="to-initialize-the-data-and-the-controls"></a>初始化資料和控制項  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下**Sheet1.vb**或**Sheet1.cs**，然後按一下 [**檢視程式碼**快顯功能表。  
  
2.  將下列程式碼加入`Sheet1_Startup`方法，以設定按鈕的文字。  
  
     [!code-vb[Trin_VstcoreDataExcel#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#15)]
     [!code-csharp[Trin_VstcoreDataExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#15)]  
  
3.  僅適用 C#，加入事件處理常式按鈕的按一下事件`Sheet1_Startup`方法。  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#16)]  
  
## <a name="adding-code-to-enable-scrolling-through-the-records"></a>加入程式碼，以啟用捲動記錄  
 將程式碼加入<xref:System.Windows.Forms.Control.Click>記錄間移動的每個按鈕事件處理常式。  
  
#### <a name="to-scroll-through-the-records"></a>捲動資料列  
  
1.  加入事件處理常式<xref:System.Windows.Forms.Control.Click>事件`Button1`，並加入下列程式碼，向後移動記錄：  
  
     [!code-vb[Trin_VstcoreDataExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#17)]
     [!code-csharp[Trin_VstcoreDataExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#17)]  
  
2.  加入事件處理常式<xref:System.Windows.Forms.Control.Click>事件`Button2`，並加入下列的程式碼，以記錄中向前推進：  
  
     [!code-vb[Trin_VstcoreDataExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet2.vb#18)]
     [!code-csharp[Trin_VstcoreDataExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet2.cs#18)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 現在您可以測試您的活頁簿，確定資料會顯示如預期般，而且您可以離線使用方案。  
  
#### <a name="to-test-the-data-caching"></a>若要測試資料的快取  
  
1.  請按 **F5**。  
  
2.  請確認已命名的範圍和清單物件會填入來自資料來源。  
  
3.  捲動的部分記錄的按鈕，即可。  
  
4.  儲存活頁簿，，，然後關閉 活頁簿和 Visual Studio。  
  
5.  停用資料庫的連接。 如果資料庫位於伺服器上，請拔除網路纜線從您的電腦，或如果資料庫是在開發電腦上停止 SQL Server 服務。  
  
6.  開啟 Excel，然後再開啟**我的主要 Detail.xlsx**從 \bin 目錄 （在 Visual Basic 中的 \My Master-Detail\bin 或 \My Master-Detail\bin\debug C# 中的）。  
  
7.  捲動瀏覽一些查看工作表運作正常中斷連線時的記錄。  
  
8.  重新連接到資料庫。 您的電腦重新連線到網路如果資料庫位於伺服器上，或如果資料庫是在開發電腦上啟動 SQL Server 服務。  
  
## <a name="next-steps"></a>後續步驟  
 這個逐步解說會顯示在工作表上建立主要/詳細資料關聯性以及快取資料集的基本概念。 接著可以執行下列一些工作：  
  
-   部署方案。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
## <a name="see-also"></a>請參閱  
 [資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [在 Office 方案中的資料](../vsto/data-in-office-solutions.md)   
 [快取資料](../vsto/caching-data.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  