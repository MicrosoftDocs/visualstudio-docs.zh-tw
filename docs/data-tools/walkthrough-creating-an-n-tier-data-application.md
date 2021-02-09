---
title: 逐步解說：建立多層式資料應用程式
description: 在這個逐步解說中，建立多層式資料應用程式。 多層式資料應用程式是存取資料，並分成許多邏輯層或層級的應用程式。
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ed395c60ec16eeff6a5aac88a99698193e8bacbd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866147"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>逐步解說：建立多層式資料應用程式
「多層式架構」(N-tier) 資料應用程式是可存取資料而且分成多個邏輯層或「層級」(tier) 的應用程式。 將應用程式元件分成離散層級，可增加應用程式的可維護性和延展性。 原因是可以更輕鬆地採用套用至單一層級的新技術，而且您不需要重新設計整個方案。 多層式架構包括呈現層、中介層和資料層。 中介層通常包括資料存取層、商務邏輯層和共用元件 (如驗證 (authentication) 和驗證 (validation))。 資料層包括關聯式資料庫。 多層式架構應用程式通常會將敏感性資訊儲存至中介層的資料存取層，以與存取呈現層的使用者隔離。 如需詳細資訊，請參閱多 [層式資料應用程式總覽](../data-tools/n-tier-data-applications-overview.md)。

其中一種在多層式架構應用程式中分為各種層級的方式，是針對您要併入應用程式中的每個層級建立離散專案。 具類型資料集所含的 `DataSet Project` 屬性可以決定所產生的資料集和 `TableAdapter` 程式碼應該進入的專案。

此逐步解說示範如何使用 [DataSet 設計工具] 將資料集和 `TableAdapter` 程式碼分成離散類別庫專案。 分隔資料集和 TableAdapter 程式碼之後，您可以 [在 Visual Studio 服務中建立 Windows Communication Foundation 服務和 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ，以呼叫資料存取層。 最後，您會建立 Windows Forms 應用程式做為展示層。 此層級會存取資料服務中的資料。

在這個逐步解說中，您將執行下列步驟：

- 建立包含多個專案的新多層式方案。

- 將兩個類別庫專案加入至多層式架構方案。

- 使用 [資料來源組態精靈]，以建立具類型資料集。

- 將產生的 [tableadapter](create-and-configure-tableadapters.md) 和資料集程式碼分成不同的專案。

- 建立要呼叫到資料存取層的 Windows Communication Foundation (WCF) 服務。

- 在服務中建立函式，以擷取資料存取層中的資料。

- 建立 Windows Forms 應用程式，以做為呈現層。

- 建立繫結至資料來源的 Windows Form 控制項。

- 撰寫程式碼以填入資料表。

![影片連結](../data-tools/media/playvideo.gif)如本主題的影片版本，請參閱[視訊 HOW TO：建立 N-Tier 資料應用程式](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90))。

## <a name="prerequisites"></a>必要條件
本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以將 SQL Server Express LocalDB 安裝為 **.net 桌面開發** 工作負載的一部分或個別元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (**SQL Server 物件總管** 會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>建立多層式方案和類別庫，以保存資料集 (DataEntityTier) 
這個逐步解說的第一個步驟是建立一個方案和兩個類別庫專案。 第一個類別庫會將資料集保存 (產生的具型 `DataSet` 別類別和 datatable，以保存應用程式的資料) 。 此專案是用做應用程式的資料實體層，而且通常位於中介層。 資料集會建立初始資料集，並自動將程式碼分隔成兩個類別庫。

> [!NOTE]
> 請確認正確命名專案和方案，然後按一下 [確定]。 這麼做可以讓您輕鬆地完成這個逐步解說。

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>建立多層式架構方案和 DataEntityTier 類別庫

1. 在 Visual Studio 中，於 [檔案]  功能表上選取 [新增]   > [專案]  。

2. 展開左側窗格中的 [ **Visual c #** ] 或 [ **Visual Basic** ]，然後選取 [ **Windows 桌面**]。

3. 在中間窗格中，選取 [ **類別庫** ] 專案類型。

4. 將專案命名為 **DataEntityTier**。

5. 將方案命名為 **NTierWalkthrough**，然後選擇 **[確定]**。

     隨即建立含有 DataEntityTier 專案的 NTierWalkthrough 方案，並將其新增至 [方案總管]。

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>建立類別庫以保存 Tableadapter (DataAccessTier) 
建立 DataEntityTier 專案之後的下一個步驟是建立另一個類別庫專案。 此專案會保存所產生的 Tableadapter，而且稱為應用程式的 *資料存取層* 。 資料存取層包含連接至資料庫所需的資訊，而且通常位於中介層。

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>為 Tableadapter 建立個別的類別庫

1. 以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增] > [新增專案]。

2. 在 [ **新增專案** ] 對話方塊的中間窗格中，選取 [ **類別庫**]。

3. 將專案命名為 **DataAccessTier** ，然後選擇 **[確定]**。

     隨即建立 DataAccessTier 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="create-the-dataset"></a>建立資料集
下一個步驟是建立具類型資料集。 具類型資料集的建立同時包含資料集類別 (包括 `DataTables`) 類別以及 `TableAdapter` 單一專案中的類別。  (所有類別都會產生到單一檔案中。當您將資料集和 Tableadapter 區分為不同的專案時，) 它是移至其他專案的資料集類別，並將 `TableAdapter` 類別留在原始專案中。 因此，在專案中建立資料集，最後會包含 Tableadapter (DataAccessTier 專案) 。 您可以使用 [ **資料來源設定]** 建立資料集。

> [!NOTE]
> 您必須具有 Northwind 範例資料庫的存取權，才能建立連接。 如需有關如何設定 Northwind 範例資料庫的詳細資訊，請參閱 [如何：安裝範例資料庫](../data-tools/installing-database-systems-tools-and-samples.md)。

### <a name="to-create-the-dataset"></a>建立資料集

1. 在 **方案總管** 中選取 **DataAccessTier** 。

2. 在 [ **資料** ] 功能表上，選取 [ **顯示資料來源**]。

   [資料來源] 視窗隨即開啟。

3. 在 [資料來源] 視窗中，選取 [新增新資料來源]，以啟動 [資料來源組態精靈]。

4. 在 [ **選擇資料來源類型** ] 頁面上，選取 [ **資料庫** ]，然後選取 **[下一步]**。

5. 在 [選擇資料連線] 頁面上，執行下列其中一項動作：

     如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選取這個資料連接。

     -或-

     選取 [ **新增連接** ] 以開啟 [ **加入連接** ] 對話方塊。

6. 如果資料庫需要密碼，請選取包含機密資料的選項，然後選擇 [ **下一步]**。

    > [!NOTE]
    > 如果您已選取本機資料庫檔案 (而非連接至 SQL Server)，則系統可能會詢問您是否要將檔案加入至專案。 選擇 [ **是]** ，將資料庫檔案加入至專案。

7. 選取 [**將連接字串儲存到應用程式佈建檔**] 頁面上的 **[下一步]** 。

8. 在 [選擇您的資料庫物件]  頁面上，展開 [資料表]  節點。

9. 選取 [ **Customers** ] 和 [ **Orders** ] 資料表的核取方塊，然後選擇 **[完成]**。

     NorthwindDataSet 會新增至 DataAccessTier 專案，並出現在 [資料來源] 視窗中。

## <a name="separate-the-tableadapters-from-the-dataset"></a>分隔 Tableadapter 與資料集
在您建立資料集之後，請分隔產生的資料集類別與 TableAdapter。 做法是將 [資料集專案] 屬性設定為在其中儲存分開之資料集類別的專案名稱。

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>分隔 TableAdapter 與資料集

1. 在 [方案總管] 中，按兩下 **NorthwindDataSet.xsd** 開啟 [DataSet 設計工具]。

2. 選取設計工具上的空白區域。

3. 在 [屬性] 視窗中，找到 [資料集專案] 節點。

4. 在 [ **資料集專案** ] 清單中，選取 [ **DataEntityTier**]。

5. 在 [建置] 功能表上，選取 [建置方案]。

   資料集和 TableAdapter 會分隔到兩個類別庫專案。 原先包含整個資料集 () 的專案 `DataAccessTier` 現在只會包含 tableadapter。 **資料集專案** 屬性中指定的專案 (`DataEntityTier`) 包含具類型的資料集： *NorthwindDataSet* (或 *NorthwindDataSet.Dataset.Designer.cs*) 。

> [!NOTE]
> 當您分隔資料集與 TableAdapter 時 (設定 [資料集專案] 屬性)，將不會自動移動專案中的現有部份資料集類別。 現有資料集部分類別必須手動移至資料集專案。

## <a name="create-a-new-service-application"></a>建立新的服務應用程式
本逐步解說示範如何使用 WCF 服務存取資料存取層，讓我們建立新的 WCF 服務應用程式。

### <a name="to-create-a-new-wcf-service-application"></a>建立新的 WCF 應用程式服務

1. 以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增] > [新增專案]。

2. 在 [ **新增專案** ] 對話方塊的左窗格中，選取 [ **WCF**]。 在中間窗格中，選取 [ **WCF 服務程式庫**]。

3. 將專案命名為 **DataService** ，然後選取 **[確定]**。

     隨即建立 DataService 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>在資料存取層中建立方法，以傳回客戶和訂單資料
資料服務必須在資料存取層中呼叫兩個方法： `GetCustomers` 和 `GetOrders` 。 這些方法會傳回 Northwind `Customers` 和 `Orders` 資料表。 `GetCustomers` `GetOrders` 在專案中建立和方法 `DataAccessTier` 。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>在資料存取層中建立可傳回 Customers 資料表的方法

1. 在 **方案總管** 中，按兩下 [ **NorthwindDataset** ] 以開啟資料集。

2. 以滑鼠右鍵按一下 **CustomersTableAdapter** ，然後按一下 [ **加入查詢**]。

3. 在 [選擇命令類型] 頁面上，保留 [使用 SQL 陳述式] 的預設值，然後按一下 [下一步]。

4. 在 [選擇查詢類型] 頁面上，保留 [傳回資料列的 SELECT] 的預設值，然後按一下 [下一步]。

5. 在 [指定 SQL SELECT 陳述式] 頁面上，保留預設查詢，然後按一下 [下一步]。

6. 在 [選擇要產生的方法] 頁面上，於 [傳回 DataTable] 區段的 [方法名稱] 中鍵入 **GetCustomers**。

7. 按一下 [完成] 。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>在資料存取層中建立可傳回 Orders 資料表的方法

1. 以滑鼠右鍵按一下 **OrdersTableAdapter**，然後按一下 [新增查詢]。

2. 在 [選擇命令類型] 頁面上，保留 [使用 SQL 陳述式] 的預設值，然後按一下 [下一步]。

3. 在 [選擇查詢類型] 頁面上，保留 [傳回資料列的 SELECT] 的預設值，然後按一下 [下一步]。

4. 在 [指定 SQL SELECT 陳述式] 頁面上，保留預設查詢，然後按一下 [下一步]。

5. 在 [選擇要產生的方法] 頁面上，於 [傳回 DataTable] 區段的 [方法名稱] 中鍵入 **GetOrders**。

6. 按一下 [完成] 。

7. 在 [建置] 功能表上，按一下 [建置方案]。

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>將資料實體和資料存取層的參考加入至資料服務
因為資料服務需要來自資料集和 TableAdapter 的資訊，所以請新增 **DataEntityTier** 和 **DataAccessTier** 專案的參考。

### <a name="to-add-references-to-the-data-service"></a>加入資料服務的參考

1. 在 [方案總管] 中，以滑鼠右鍵按一下 **DataService**，然後按一下 [新增參考]。

2. 在 [新增參考] 對話方塊中，按一下 [專案] 索引標籤。

3. 選取 **DataAccessTier** 和 **DataEntityTier** 專案。

4. 按一下 [確定]  。

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>將函數新增至服務，以在資料存取層中呼叫 GetCustomers 和 GetOrders 方法
現在，資料存取層包含方法可以傳回資料、在資料服務中建立方法以呼叫資料存取層中的方法。

> [!NOTE]
> 針對 C# 專案，您必須加入下列程式碼的 `System.Data.DataSetExtensions` 組件參考以進行編譯。

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>在資料服務中建立 GetCustomers 和 GetOrders 函式

1. 在 **DataService** 專案中，按兩下 **IService1.vb** 或 **IService1.cs**。

2. 在 [在此新增您的服務作業] 註解下方，新增下列程式碼：

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

3. 在 DataService 專案中，按兩下 **Service1.vb** (或 **Service1.cs**)。

4. 將下列程式碼新增至 **Service1** 類別：

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

5. 在 [建置] 功能表上，按一下 [建置方案]。

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>建立展示層以顯示資料服務中的資料
既然解決方案包含的資料服務具有可呼叫資料存取層的方法，請建立另一個專案來呼叫資料服務，並向使用者呈現資料。 在這個逐步解說中，建立 Windows Form 應用程式；這是多層式架構應用程式的呈現層。

### <a name="to-create-the-presentation-tier-project"></a>建立呈現層專案

1. 以滑鼠右鍵按一下 [方案總管] 中的解決方案，然後選擇 [新增] > [新增專案]。

2. 在 [ **新增專案** ] 對話方塊的左窗格中，選取 [ **Windows 桌面**]。 在中間窗格中，選取 [ **Windows Forms 應用程式**]。

3. 將專案命名為 **PresentationTier**，然後按一下 [確定]。

    隨即建立 PresentationTier 專案，並將它加入至 NTierWalkthrough 方案。

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>將 PresentationTier 專案設定為啟始專案
我們會將 **PresentationTier** 專案設定為方案的啟始專案，因為這是呈現和與資料互動的實際用戶端應用程式。

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>將新的呈現層專案設定為啟始專案

- 在 [方案總管] 中，以滑鼠右鍵按一下 **PresentationTier**，然後按一下 [設定為啟始專案]。

## <a name="add-references-to-the-presentation-tier"></a>將參考新增至展示層
用戶端應用程式 PresentationTier 需要有資料服務的服務參考，才能存取服務中的方法。 此外，還需要有資料集參考，才能透過 WCF 服務啟用類型共用。 在您透過資料服務啟用類型共用之前，展示層無法使用加入至部分資料集類別的程式碼。 因為您通常會將程式碼（例如驗證程式代碼）加入資料列和資料行變更資料表的事件，所以您可能會想要從用戶端存取此程式碼。

### <a name="to-add-a-reference-to-the-presentation-tier"></a>加入呈現層的參考

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **PresentationTier** ，然後選取 [ **加入參考**]。

2. 在 [ **加入參考** ] 對話方塊中，選取 [ **專案** ] 索引標籤。

3. 選取 [ **DataEntityTier** ]，然後選擇 **[確定]**。

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>加入呈現層的服務參考

1. 在 **方案總管** 中，以滑鼠右鍵按一下 **PresentationTier** ，然後選取 [ **加入服務參考**]。

2. 在 [ **加入服務參考** ] 對話方塊中，選取 [ **探索**]。

3. 選取 [ **Service1** ]，然後選擇 **[確定]**。

    > [!NOTE]
    > 如果您在目前的電腦上有多個服務，請選取您先前在本逐步解說中建立的服務， (包含 `GetCustomers` 和 `GetOrders` 方法) 的服務。

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>將 Datagridviews 加入新增至表單，以顯示資料服務所傳回的資料
在您新增資料服務的服務參考之後，會將服務所傳回的資料自動填入 [資料來源] 視窗。

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>將兩個繫結 DataGridViews 的資料加入至表單

1. 在 [方案總管] 中，選取 **PresentationTier** 專案。

2. 在 [資料來源] 視窗中，展開 **NorthwindDataSet**，並找到 [客戶] 節點。

3. 將 [客戶] 節點拖曳至 Form1。

4. 在 [資料來源] 視窗中，展開 [客戶] 節點，並找到相關的 [訂單] 節點 (巢狀於 [客戶] 節點中的 [訂單] 節點)。

5. 將相關的 [訂單] 節點拖曳至 Form1。

6. 按兩下表單的空白區域，以建立 `Form1_Load` 事件處理常式。

7. 將下列程式碼加入至 `Form1_Load` 事件處理常式。

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

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>增加服務所允許的訊息大小上限
的預設值不夠 `maxReceivedMessageSize` 大，無法容納取自 `Customers` 和資料表的資料 `Orders` 。 在下列步驟中，您會將此值增加為6553600。 您可以變更用戶端上的值，此值會自動更新服務參考。

> [!NOTE]
> 較小的預設大小是要限制拒絕服務 (DoS) 攻擊的機率。 如需詳細資訊，請參閱<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>。

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>增加 maxReceivedMessageSize 值

1. 在 [方案總管] 中，按兩下 **PresentationTier** 專案中的 **app.config** 檔案。

2. 找到 **maxReceivedMessage** 大小屬性，並將值變更為 `6553600`。

## <a name="test-the-application"></a>測試應用程式
按 **F5** 鍵執行應用程式。 和資料表中的 `Customers` 資料 `Orders` 會從資料服務中取出並顯示在表單上。

## <a name="next-steps"></a>下一步
視應用程式的需求而定，在您儲存 Windows 應用程式中的關聯資料後，可能還要執行幾個步驟。 例如，您可以對此應用程式進行下列增強：

- 將驗證加入至資料集。

- 將其他方法加入至服務，以將資料更新回資料庫。

## <a name="see-also"></a>另請參閱

- [使用多層式架構 (N-Tier) 應用程式中的資料集](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [階層式更新](../data-tools/hierarchical-update.md)
- [存取 Visual Studio 中的資料](../data-tools/accessing-data-in-visual-studio.md)
