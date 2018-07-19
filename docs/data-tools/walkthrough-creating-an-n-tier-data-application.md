---
title: 逐步解說：建立 N-Tier 資料應用程式
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 007a0a85bf9d7200860194b881a3d0505f6bee45
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175339"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>逐步解說： 建立 n-tier 資料應用程式
*多層式架構*資料應用程式是應用程式存取資料而且分成多個邏輯層，或*層*。 將應用程式元件分成離散層級，可增加應用程式的可維護性和延展性。 原因是可以更輕鬆地採用套用至單一層級的新技術，而且您不需要重新設計整個方案。 多層式架構包括呈現層、中介層和資料層。 中介層通常包括資料存取層、商務邏輯層和共用元件 (如驗證 (authentication) 和驗證 (validation))。 資料層包括關聯式資料庫。 多層式架構應用程式通常會將敏感性資訊儲存至中介層的資料存取層，以與存取呈現層的終端使用者隔離。 如需詳細資訊，請參閱 <<c0> [ 多層式架構資料應用程式概觀](../data-tools/n-tier-data-applications-overview.md)。

其中一種在多層式架構應用程式中分為各種層級的方式，是針對您要併入應用程式中的每個層級建立離散專案。 具類型資料集所含的 `DataSet Project` 屬性可以決定所產生的資料集和 `TableAdapter` 程式碼應該進入的專案。

本逐步解說示範如何以不同的資料集和`TableAdapter`程式碼分成離散類別庫專案，使用**Dataset 設計工具**。 您可將資料集和 TableAdapter 程式碼之後，您會建立[Windows Communication Foundation 服務和 Visual Studio 中的 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)来呼叫到資料存取層的服務。 最後，您會建立為呈現層的 Windows Forms 應用程式。 此層級會存取資料服務中的資料。

在本逐步解說中，您可以執行下列步驟：

-   建立新的多層式架構方案包含多個專案。

-   將兩個類別庫專案加入至多層式架構方案。

-   使用建立具類型資料集**資料來源組態精靈**。

-   將產生[TableAdapters](create-and-configure-tableadapters.md)和資料集的程式碼分成離散專案。

-   建立要呼叫到資料存取層的 Windows Communication Foundation (WCF) 服務。

-   在服務中建立函式，以擷取資料存取層中的資料。

-   建立 Windows Form 應用程式，以做為呈現層。

-   建立繫結至資料來源的 Windows Form 控制項。

-   撰寫程式碼以填入資料表。

![影片連結](../data-tools/media/playvideo.gif)如本主題的影片版本，請參閱 <<c2> [ 影片-如何： 建立 n-tier 資料應用程式](http://go.microsoft.com/fwlink/?LinkId=115188)。

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分 **.NET 桌面開發**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (**SQL Server 物件總管**安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>建立多層式架構方案和類別庫，以保留資料集 (DataEntityTier)
 這個逐步解說的第一個步驟是建立一個方案和兩個類別庫專案。 第一個類別庫會保留資料集 (產生的具類型`DataSet`類別和保存應用程式的資料的 DataTables)。 此專案是用做應用程式的資料實體層，而且通常位於中介層。 資料集建立初始資料集，並自動將程式碼分為兩個類別程式庫。

> [!NOTE]
>  請務必正確地命名專案和方案為再按一下 **確定**。 這麼做可以讓您輕鬆地完成這個逐步解說。

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>建立多層式架構方案和 DataEntityTier 類別庫

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 展開  **Visual C#** 或是**Visual Basic**的左側窗格中，然後選取**Windows Desktop**。

3. 在中間窗格中，選取**類別庫**專案類型。

4. 將專案命名為**DataEntityTier**。

5. 將方案命名為**NTierWalkthrough**，然後選擇**確定**。

     會建立含有 DataEntityTier 專案的 NTierWalkthrough 方案，並將其加入**方案總管 中**。

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>建立類別庫以保留 Tableadapter (DataAccessTier)
 建立 DataEntityTier 專案之後的下一個步驟是建立另一個類別庫專案。 此專案會保留產生的 Tableadapter，並呼叫*資料存取層*應用程式。 資料存取層包含連接至資料庫所需的資訊，而且通常位於中介層。

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Tableadapter 建立個別的類別庫

1.  在方案上按一下滑鼠右鍵**方案總管**，然後選擇**新增** > **新專案**。

2.  在 **新的專案**對話方塊中，在中間窗格中，選取**類別庫**。

3.  將專案命名為**DataAccessTier** ，然後選擇**確定**。

     隨即建立 DataAccessTier 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="create-the-dataset"></a>建立資料集
 下一個步驟是建立具類型資料集。 這兩個資料集類別以建立具類型資料集 (包括`DataTables`類別) 和`TableAdapter`單一專案中的類別。 (所有類別都會產生到單一檔案)。當您將資料集和 Tableadapter 分成不同的專案時，就會移至另一個專案，讓資料集類別`TableAdapter`原始專案中的類別。 因此，最後會包含 Tableadapter （DataAccessTier 專案） 的專案中建立資料集。 使用建立資料集**資料來源組態精靈**。

> [!NOTE]
>  您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需有關如何設定 Northwind 範例資料庫的資訊，請參閱 <<c0> [ 如何： 安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

### <a name="to-create-the-dataset"></a>建立資料集

1.  選取 [ **DataAccessTier**中**方案總管] 中**。

2.  在 **資料**功能表上，選取**顯示資料來源**。

3.  在 **資料來源**視窗中，選取**加入新的資料來源**來啟動**資料來源組態精靈**。

4.  在 [**選擇資料來源類型**頁面上，選取**資料庫**，然後選取**下一步]**。

5.  在 **選擇資料連接**頁面上，執行下列動作之一：

     如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

     -或-

     選取 [**新的連線**以開啟**加入連接**] 對話方塊。

6.  如果資料庫需要密碼，請選取選項來加入敏感性資料，然後選擇**下一步**。

    > [!NOTE]
    >  如果您已選取本機資料庫檔案 (而非連接至 SQL Server)，則系統可能會詢問您是否要將檔案加入至專案。 選擇**是**將資料庫檔案加入至專案。

7.  選取 **下一步**上**將連接字串儲存到應用程式組態檔**頁面。

8.  在 [選擇您的資料庫物件]  頁面上，展開 [資料表]  節點。

9.  選取核取方塊**客戶**並**訂單**資料表，然後選擇**完成**。

     NorthwindDataSet 會加入至 DataAccessTier 專案，而且會出現在**Zdroje dat**視窗。

## <a name="separate-the-tableadapters-from-the-dataset"></a>分隔 Tableadapter 與資料集
 在您建立資料集之後，請分隔產生的資料集類別與 TableAdapter。 您可以設定**資料集 Project**屬性，以在其中儲存分開之資料集類別的專案的名稱。

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>分隔 TableAdapter 與資料集

1.  按兩下**NorthwindDataSet.xsd**中**方案總管**若要開啟中的資料集**Dataset 設計工具**。

2.  選取設計工具上的空白區域。

3.  找出**資料集 Project**中的節點**屬性**視窗。

4.  在 **資料集 Project**清單中，選取**DataEntityTier**。

5.  在 [建置] 功能表上，選取 [建置方案]。

 資料集和 TableAdapter 會分隔到兩個類別庫專案。 原本包含整個資料集的專案 (`DataAccessTier`) 現在只會包含 Tableadapter。 中指定的專案**資料集 Project**屬性 (`DataEntityTier`) 包含具類型資料集： *NorthwindDataSet.Dataset.Designer.vb* (或*NorthwindDataSet.Dataset.Designer.cs*)。

> [!NOTE]
>  當您分隔資料集和 Tableadapter (藉由設定**資料集 Project**屬性)，在專案中的現有部份資料集類別不會自動移動。 現有資料集部分類別必須手動移至資料集專案。

## <a name="create-a-new-service-application"></a>建立新的服務應用程式
本逐步解說示範如何使用 WCF 服務來存取資料存取層，讓我們建立新的 WCF 服務應用程式。

### <a name="to-create-a-new-wcf-service-application"></a>建立新的 WCF 應用程式服務

1.  在方案上按一下滑鼠右鍵**方案總管**，然後選擇**新增** > **新專案**。

2.  在 **新的專案**對話方塊中，在左側窗格中，選取**WCF**。  在中間窗格中，選取**WCF 服務程式庫**。

3.  將專案命名為**DataService** ，然後選取**確定**。

     隨即建立 DataService 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>在 資料存取層，以傳回 customers 及 orders 資料建立方法
 資料服務必須在資料存取層中呼叫兩個方法：`GetCustomers`和`GetOrders`。 這些方法會傳回 Northwind`Customers`和`Orders`資料表。 建立`GetCustomers`並`GetOrders`中的方法`DataAccessTier`專案。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>在資料存取層中建立可傳回 Customers 資料表的方法

1.  在 **方案總管**，按兩下**NorthwindDataset.xsd**開啟資料集。

2.  以滑鼠右鍵按一下**CustomersTableAdapter**然後按一下**加入查詢**。

3.  在 [**選擇命令類型**頁面上，保留預設值**使用 SQL 陳述式**然後按一下**下一步]**。

4.  在上**選擇查詢類型**頁面上，保留預設值**會傳回資料列選取**，按一下 [**下一步]**。

5.  在 [**指定 SQL SELECT 陳述式**頁面上，保留預設查詢，然後按一下**下一步]**。

6.  在上**選擇要產生的方法**頁面上，輸入**GetCustomers** for**方法名稱**中**傳回 DataTable**一節。

7.  按一下 [ **完成**]。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>在資料存取層中建立可傳回 Orders 資料表的方法

1.  以滑鼠右鍵按一下**OrdersTableAdapter**然後按一下**加入查詢**。

2.  在 [**選擇命令類型**頁面上，保留預設值**使用 SQL 陳述式**然後按一下**下一步]**。

3.  在上**選擇查詢類型**頁面上，保留預設值**會傳回資料列選取**，按一下 [**下一步]**。

4.  在 [**指定 SQL SELECT 陳述式**頁面上，保留預設查詢，然後按一下**下一步]**。

5.  在上**選擇要產生的方法**頁面上，輸入**GetOrders** for**方法名稱**中**傳回 DataTable**一節。

6.  按一下 [ **完成**]。

7.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>加入資料服務中的資料實體的參考和資料存取層
 因為資料服務需要來自資料集和 Tableadapter 的資訊，請將參考加入至**DataEntityTier**並**DataAccessTier**專案。

### <a name="to-add-references-to-the-data-service"></a>加入資料服務的參考

1.  以滑鼠右鍵按一下**DataService**中**方案總管**然後按一下**加入參考**。

2.  按一下 [**專案**索引標籤中**加入參考**] 對話方塊。

3.  選取這兩個**DataAccessTier**並**DataEntityTier**專案。

4.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>將函式新增至服務，以在資料存取層中呼叫 GetCustomers 和 GetOrders 方法
 現在，資料存取層包含方法可以傳回資料、在資料服務中建立方法以呼叫資料存取層中的方法。

> [!NOTE]
>  針對 C# 專案，您必須加入下列程式碼的 `System.Data.DataSetExtensions` 組件參考以進行編譯。

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>在資料服務中建立 GetCustomers 和 GetOrders 函式

1.  在  **DataService**專案中，按兩下**IService1.vb**或是**IService1.cs**。

2.  新增下列程式碼底下**新增您的服務作業**註解：

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3.  在 DataService 專案中，按兩下**Service1.vb** (或**Service1.cs**)。

4.  將下列程式碼加入**Service1**類別：

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5.  在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>建立呈現層以顯示來自資料服務的資料
 現在，此方案包含的方法的呼叫到資料存取層、 建立資料服務會呼叫的另一個專案和資料呈現給使用者的資料服務。 在這個逐步解說中，建立 Windows Forms 應用程式；這是多層式架構應用程式的呈現層。

### <a name="to-create-the-presentation-tier-project"></a>建立呈現層專案

1.  在方案上按一下滑鼠右鍵**方案總管**，然後選擇**新增** > **新專案**。

2.  在 **新的專案**對話方塊中，在左側窗格中，選取**Windows Desktop**。 在中間窗格中，選取**Windows Forms 應用程式**。

3.  將專案命名為**PresentationTier**然後按一下**確定**。

    隨即建立 PresentationTier 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>將 PresentationTier 專案設定為啟始專案
我們會設定**PresentationTier**為方案的啟始專案，因為它是呈現，並與資料互動的實際用戶端應用程式的專案。

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>若要設定新的呈現層專案為啟始專案

-   在 **方案總管**，以滑鼠右鍵按一下**PresentationTier** ，按一下 **設定為啟始專案**。

## <a name="add-references-to-the-presentation-tier"></a>將參考加入至展示層
 用戶端應用程式中，於 PresentationTier 需要資料服務的服務參考才能存取服務中的方法。 此外，還需要有資料集參考，才能透過 WCF 服務啟用類型共用。 直到您啟用類型共用透過資料服務時，程式碼加入至部分資料集類別不適用於展示層。 因為您通常會加入程式碼，例如驗證程式碼加入的資料列和資料行變更事件資料表的資料，很可能您會想要從用戶端存取此程式碼。

### <a name="to-add-a-reference-to-the-presentation-tier"></a>加入呈現層的參考

1.  在 [**方案總管] 中**，以滑鼠右鍵按一下**PresentationTier** ，然後選取**加入參考**。

2.  在 [**加入參考**對話方塊中，選取**專案**] 索引標籤。

3.  選取  **DataEntityTier** ，然後選擇**確定**。

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>加入呈現層的服務參考

1.  在 **方案總管**，以滑鼠右鍵按一下**PresentationTier** ，然後選取**加入服務參考**。

2.  在 **加入服務參考**對話方塊中，選取**Discover**。

3.  選取  **Service1** ，然後選擇**確定**。

    > [!NOTE]
    >  如果您有多個服務，目前的電腦上，選取您先前在本逐步解說中建立的服務 (服務，其中包含`GetCustomers`和`GetOrders`方法)。

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>將 DataGridViews 加入至表單以顯示資料服務所傳回的資料
 加入服務參考加入資料服務之後, **Zdroje dat**視窗會自動填入服務所傳回的資料。

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>將兩個繫結 DataGridViews 的資料加入至表單

1.  在 **方案總管**，選取**PresentationTier**專案。

2.  在 [**資料來源**] 視窗中，展開**NorthwindDataSet**並找出**客戶**節點。

3.  拖曳**客戶**節點拖曳至 Form1。

4.  在 [**資料來源**] 視窗中，展開**客戶**節點並找到相關**訂單**節點 (**訂單**巢狀於**客戶**節點)。

5.  將相關**訂單**節點拖曳至 Form1。

6.  按兩下表單的空白區域，以建立 `Form1_Load` 事件處理常式。

7.  將下列程式碼加入至 `Form1_Load` 事件處理常式。

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>增加服務允許的最大訊息大小
預設值`maxReceivedMessageSize`不夠大，無法保存從擷取的資料`Customers`和`Orders`資料表。 在下列步驟中，您將會增加為 6553600 值。 您變更在用戶端，會自動更新服務參考的值。

> [!NOTE]
>  較小的預設大小是要限制拒絕服務 (DoS) 攻擊的機率。 如需詳細資訊，請參閱<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>。

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>增加 maxReceivedMessageSize 值

1.  在 **方案總管**，按兩下**app.config**檔案中**PresentationTier**專案。

2.  找出**maxReceivedMessage**大小屬性，並將值變更為`6553600`。

## <a name="test-the-application"></a>測試應用程式
執行應用程式藉由按下**F5**。 將資料從`Customers`和`Orders`資料表從資料服務中擷取並顯示在表單上。

## <a name="next-steps"></a>後續步驟
 根據應用程式需求，當您在 Windows 應用程式中儲存相關資料之後，可能會有幾個想要執行的步驟。 例如，您可以對此應用程式進行下列增強：

-   將驗證加入至資料集。

-   將其他方法加入至服務，以將資料更新回資料庫。

## <a name="see-also"></a>另請參閱

- [使用多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)