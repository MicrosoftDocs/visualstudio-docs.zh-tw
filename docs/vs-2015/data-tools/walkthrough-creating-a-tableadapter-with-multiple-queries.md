---
title: 逐步解說： 以多個查詢建立 TableAdapter |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: e48750cf876f561b25802fd20b1e270215a1b605
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47491242"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>逐步解說：以多個查詢建立 TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本逐步解說中，您將建立資料集，使用 TableAdapter[資料來源組態精靈](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)。 本逐步解說會引導您完成建立中的第二個查詢的程序[TableAdapter](../data-tools/tableadapter-overview.md)使用[編輯 TableAdapters](../data-tools/editing-tableadapters.md)內[Dataset 設計工具](../data-tools/creating-and-editing-typed-datasets.md)。  
  
 這個逐步解說中所述的工作包括：  
  
-   建立新**Windows 應用程式**專案。  
  
-   建立和設定應用程式中的資料來源，藉由建置具有的資料集**資料來源組態精靈**。  
  
-   開啟中的新資料集**Dataset 設計工具**。  
  
-   將查詢加入至 TableAdapter **TableAdapter 查詢組態精靈**。  
  
## <a name="prerequisites"></a>必要條件  
 若要完成這個逐步解說，您需要：  
  
-   Northwind 範例資料庫的存取權 (SQL Server 或 Access 版本)。 如需詳細資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
## <a name="creating-a-new-windows-application"></a>建立新的 Windows 應用程式  
 第一個步驟是建立 Windows 應用程式。  
  
#### <a name="to-create-a-new-windows-application-project"></a>建立新的 Windows 應用程式專案  
  
1.  在 [ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，從**檔案**] 功能表中，建立新的專案。  
  
2.  選擇程式設計語言**專案類型**窗格。  
  
3.  按一下  **Windows 應用程式**中**範本**窗格。  
  
4.  將專案命名為`TableAdapterQueriesWalkthrough`，然後按一下 **[確定]**。  
  
     Visual Studio 將專案加入**方案總管 中**並顯示新的表單設計工具中。  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>使用 TableAdapter 建立資料庫資料來源  
 這個步驟會建立使用資料來源**資料來源組態精靈**根據`Customers`Northwind 範例資料庫中的資料表。 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需設定 Northwind 範例資料庫的詳細資訊，請參閱[如何： 安裝範例資料庫](../data-tools/how-to-install-sample-databases.md)。  
  
#### <a name="to-create-the-data-source"></a>若要建立資料來源  
  
1.  按一下 [ **資料** ] 功能表上的 [ **顯示資料來源**]。  
  
2.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態精靈**。  
  
3.  請選取 [ **選擇資料來源類型** ] 頁面上的 [ **資料庫** ]，再按 [ **下一步**]。  
  
4.  在 **選擇您的資料連接**頁面上，執行下列其中之一：  
  
    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。  
  
         -或-  
  
    -   選取 [**新的連線**來啟動**加入/修改連接**] 對話方塊。  
  
5.  如果您的資料庫需要密碼，請選取選項來加入敏感性資料，然後按一下**下一步**。  
  
6.  按一下 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。  
  
7.  依序展開**資料表**上的節點**選擇您的資料庫物件**頁面。  
  
8.  選取 **客戶**資料表，然後按一下**完成**。  
  
     **NorthwindDataSet**新增至您的專案並**客戶**資料表會出現在**Zdroje dat**視窗。  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>在 DataSet 設計工具中開啟資料集  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>在 DataSet 設計工具中開啟資料集  
  
1.  以滑鼠右鍵按一下**NorthwindDataset**中**Zdroje dat**視窗。  
  
2.  在捷徑功能表，選擇**以設計工具編輯資料集**。  
  
     在中開啟 NorthwindDataset **Dataset 設計工具**。  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>將第二個查詢加入至 CustomersTableAdapter  
 精靈所建立的資料集**客戶**資料表並**CustomersTableAdapter**。 本逐步解說此區段會新增至第二項查詢**CustomersTableAdapter**。  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>將查詢加入至 CustomersTableAdapter  
  
1.  拖曳**查詢**從**資料集**索引標籤**工具箱**拖曳至**客戶**資料表。  
  
     [編輯 TableAdapters](../data-tools/editing-tableadapters.md)隨即開啟。  
  
2.  選取 [**使用 SQL 陳述式**，然後按一下**下一步]**。  
  
3.  選取 [**會傳回資料列選取**，然後按一下**下一步]**。  
  
4.  將 WHERE 子句加入至查詢，使它如下所示：  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  如果您使用 Access 版本的 Northwind，取代@City加上問號的參數。 (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  在 **選擇要產生的方法**頁面上，命名**填入 DataTable**方法`FillByCity`。  
  
    > [!NOTE]
    >  方法**傳回 DataTable**未使用在本逐步解說中，所以您可以清除此核取方塊，或保留預設名稱。  
  
6.  按一下 [**下一步]** 並完成精靈。  
  
     **FillByCity**查詢隨即加入至**CustomersTableAdapter**。  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>加入程式碼以在表單上執行其他查詢  
  
#### <a name="to-execute-the-query"></a>查詢查詢  
  
1.  選取  **Form1**中**方案總管**，然後按一下**檢視表設計工具**。  
  
2.  拖曳**客戶**從節點**Zdroje dat**視窗**Form1**。  
  
3.  變更為程式碼檢視中，選取**程式碼**從**檢視**功能表。  
  
4.  將 `Form1_Load` 事件處理常式中的程式碼取代為下列程式碼，以執行 `FillByCity` 查詢。  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>執行應用程式  
  
#### <a name="to-run-the-application"></a>若要執行應用程式  
  
-   按 F5。  
  
-   此方格會填入 `City` 值為 `Seattle` 的客戶。  
  
## <a name="next-steps"></a>後續步驟  
  
### <a name="to-add-functionality-to-your-application"></a>加入應用程式的功能  
  
-   加入 <xref:System.Windows.Forms.TextBox> 控制項和 <xref:System.Windows.Forms.Button> 控制項，並將文字方塊中的值傳遞給查詢。 (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`)  
  
-   將驗證邏輯加入至資料集內資料表的 <xref:System.Data.DataTable.ColumnChanging> 或 <xref:System.Data.DataTable.RowChanging> 事件。 如需詳細資訊，請參閱 <<c0> [ 驗證資料集中](../data-tools/validate-data-in-datasets.md)。  
  
## <a name="see-also"></a>另請參閱  
 [TableAdapter 概觀](../data-tools/tableadapter-overview.md)   
 [建立和設定 Tableadapter](../data-tools/create-and-configure-tableadapters.md)   
 [如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)   
 [資料逐步解說](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)   
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [將資料擷取至您的應用程式](../data-tools/fetching-data-into-your-application.md)   
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)