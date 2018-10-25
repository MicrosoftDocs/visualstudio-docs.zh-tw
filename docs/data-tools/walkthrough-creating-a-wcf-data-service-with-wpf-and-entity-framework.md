---
title: 逐步解說： 使用 WPF 和 Entity Framework 建立 WCF 資料服務
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 082fe68979ea7ae6a0c0655b7731aa8c7c9f3ac5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838760"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>逐步解說： 使用 WPF 和 Entity Framework 建立 WCF 資料服務
本逐步解說示範如何建立簡單[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]裝載在[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]web 應用程式，然後將它存取 Windows Form 應用程式。

在本逐步解說您：

- 建立 web 應用程式，以裝載[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]。

- 建立[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]表示`Customers`Northwind 資料庫中的資料表。

- 建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]。

- 建立用戶端應用程式，並加入 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的參考。

- 啟用對服務的資料繫結，並產生使用者介面。

- 您可以選擇在應用程式中加入篩選功能。

## <a name="prerequisites"></a>必要條件
本逐步解說會使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1.  如果您沒有 SQL Server Express LocalDB，請將它安裝從[SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)，或透過**Visual Studio 安裝程式**。 在  **Visual Studio 安裝程式**，您可以安裝 SQL Server Express LocalDB 做為一部分**資料儲存和處理**工作負載，或作為個別的元件。

2.  安裝 Northwind 範例資料庫執行下列步驟：

    1. 在 Visual Studio 中開啟**SQL Server 物件總管**視窗。 (**SQL Server 物件總管**安裝的一部分**資料儲存和處理**Visual Studio 安裝程式中的工作負載。)依序展開**SQL Server**節點。 以滑鼠右鍵按一下您的 LocalDB 執行個體，然後選取**新的查詢**。

       查詢編輯器視窗隨即開啟。

    2. 複製[Northwind 的 TRANSACT-SQL 指令碼](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)到剪貼簿。 這個 T-SQL 指令碼會從頭建立 Northwind 資料庫，並填入資料。

    3. 將 T-SQL 指令碼貼到查詢編輯器，然後選擇**Execute**  按鈕。

       短時間之後，查詢完成執行，並建立 Northwind 資料庫。

## <a name="creating-the-service"></a>建立服務
若要建立[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，您會加入一個 web 專案，請建立[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]，然後從模型中建立服務。

在第一個步驟中，您可以新增 web 專案來裝載服務。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>若要建立 web 專案

1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。

2.  在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#** 和**Web**節點，然後選擇  **ASP.NET Web 應用程式**範本。

3.  在 [**名稱**文字方塊中，輸入**NorthwindWeb**，然後選擇 **[確定]** ] 按鈕。

4.  中**新增 ASP.NET 專案**對話方塊中，於**選取範本**清單中，選擇**空**，然後選擇 **[確定]** 按鈕。

在下一個步驟中，您會建立[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]表示`Customers`Northwind 資料庫中的資料表。

### <a name="to-create-the-entity-data-model"></a>若要建立實體資料模型

1.  在功能表列中，選擇 [專案] > [加入新項目]。

2.  在**加入新項目**對話方塊方塊中，選擇**資料**節點，然後選擇**ADO.NET 實體資料模型**項目。

3.  在 **名稱**文字方塊中，輸入`NorthwindModel`，然後選擇**新增**按鈕。

     [實體資料模型精靈] 隨即出現。

4.  在 [實體資料模型精靈] 中，在**選擇模型內容**頁面上，選擇**資料庫的 EF Designer**項目，然後再選擇 [**下一步]** 按鈕。

5.  在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：

    -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選擇這個資料連接。

         -或-

    -   選擇**新的連接**，設定新的資料連接 按鈕。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。

6.  如果資料庫需要密碼，請選擇**是，連接字串中包括敏感性資料**選項按鈕，然後再選擇**下一步**  按鈕。

    > [!NOTE]
    > 如果出現對話方塊，請選擇**是**將檔案儲存至您的專案。

7.  在 **選擇您的版本**頁面上，選擇**Entity Framework 5.0**選項按鈕，然後選擇**下一步**  按鈕。

    > [!NOTE]
    > 若要使用最新版的 Entity Framework 6 與 WCF 服務，您必須安裝 WCF Data Services Entity Framework 提供者 NuGet 封裝。 請參閱[使用 WCF Data Services 5.6.0 和 Entity Framework 6 +](https://blogs.msdn.microsoft.com/odatateam/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6/)。

8.  在上**選擇您的資料庫物件**頁面上，展開**資料表**節點中，選取**客戶**核取方塊，，然後選擇**完成**按鈕。

     實體模型圖表會顯示，並*NorthwindModel.edmx*檔案新增至您的專案。

在下一個步驟中，您可以建立和測試資料服務。

### <a name="to-create-the-data-service"></a>若要建立資料服務

1.  在功能表列中，選擇 [專案] > [加入新項目]。

2.  在**加入新項目**對話方塊方塊中，選擇**Web**節點，然後選擇**WCF Data Service 5.6**項目。

3.  在 **名稱**文字方塊中，輸入`NorthwindCustomers`，然後選擇**新增**按鈕。

     **NorthwindCustomers.svc**檔案會出現在**程式碼編輯器**。

4.  在 **程式碼編輯器**，找出第一個`TODO:`註解，並以下列程式碼取代：

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  將 `InitializeService` 事件處理常式中的註解以下列程式碼取代：

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  在功能表列上選擇 **偵錯** > **啟動但不偵錯**來執行服務。 瀏覽器視窗隨即開啟並顯示服務的 XML 結構描述。

7.  中**位址**列上，輸入`Customers`的 URL 結尾處**NorthwindCustomers.svc**，然後選擇**Enter**索引鍵。

     中的資料的 XML 表示法`Customers`資料表隨即出現。

    > [!NOTE]
    > 在某些情況中，Internet Explorer 會將資料錯譯為 RSS 摘要 (RSS Feed)。 您必須確定顯示 RSS 摘要的選項已停用。 如需詳細資訊，請參閱 <<c0> [ 疑難排解服務參考](../data-tools/troubleshooting-service-references.md)。

8.  關閉瀏覽器視窗。

在下一個步驟中，您可以建立 Windows Form 用戶端應用程式來取用服務。

## <a name="creating-the-client-application"></a>建立用戶端應用程式
 若要建立用戶端應用程式，您新增第二個專案、 加入服務參考加入專案設定為資料來源，並建立使用者介面，以顯示來自服務的資料。

 在第一個步驟中，您可以將 Windows Form 專案加入方案，並將它設定為啟始專案。

### <a name="to-create-the-client-application"></a>若要建立用戶端應用程式

1.  在功能表列上選擇 [檔案]**新增** > **新專案**。

2.  中**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#**  節點，選擇**Windows**  節點，然後選擇  **Windows Forms 應用程式**。

3.  在 [名稱] 文字方塊中，輸入 `NorthwindClient`，然後選擇 [確定] 按鈕。

4.  在 **方案總管**，選擇**NorthwindClient**專案節點。

5.  在功能表列上選擇 **專案**，**設定為啟始專案**。

您可以在下一個步驟中，加入服務參考[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]web 專案中。

### <a name="to-add-a-service-reference"></a>若要加入服務參考

1.  在功能表列上選擇 **專案** > **加入服務參考**。

2.  在 [**加入服務參考**對話方塊方塊中，選擇**Discover** ] 按鈕。

     NorthwindCustomers 服務的 URL 會出現在**地址**欄位。

3.  選擇**確定**按鈕以新增服務參考。

在下一個步驟中，您可以設定要啟用資料繫結至服務的資料來源。

### <a name="to-enable-data-binding-to-the-service"></a>若要啟用對服務的資料繫結

1.  在功能表列上選擇 **檢視** > **其他 Windows** > **Zdroje dat**。

2.  在 **資料來源** 視窗中，選擇**加入新的資料來源** 按鈕。

3.  上**選擇資料來源類型**頁面**資料來源組態精靈**，選擇**物件**，然後選擇**下一步**按鈕.

4.  在上**選取資料物件**頁面上，展開**NorthwindClient**節點，然後展開**NorthwindClient.ServiceReference1**節點。

5.  選取 [**客戶**核取方塊，然後再選擇**完成**] 按鈕。

在下一個步驟中，您可以建立使用者介面，顯示來自服務的資料。

### <a name="to-create-the-user-interface"></a>若要建立使用者介面

1. 在 **資料來源** 視窗中，開啟捷徑功能表**客戶**節點，然後選擇 **複製**。

2. 在  **Form1.vb**或是**Form1.cs**表單設計工具，開啟捷徑功能表，然後選擇**貼上**。

    表單中會加入一個 <xref:System.Windows.Forms.DataGridView> 控制項、一個 <xref:System.Windows.Forms.BindingSource> 元件，和一個 <xref:System.Windows.Forms.BindingNavigator> 元件。

3. 選擇**CustomersDataGridView**控制項，然後在**屬性** 視窗中設定**停駐**屬性設**填滿**。

4. 在**方案總管**，開啟捷徑功能表**Form1**節點，然後選擇 **檢視程式碼**以開啟程式碼編輯器，並新增下列`Imports`或`Using`陳述式在檔案頂端：

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. 將下列程式碼加入至 `Form1_Load` 事件處理常式：

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
           Dim proxy As New NorthwindEntities _
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
           Me.CustomersBindingSource.DataSource = proxy.Customers
       End Sub
   ```

   ```csharp
   private void Form1_Load(object sender, EventArgs e)
   {
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
   this.CustomersBindingSource.DataSource = proxy.Customers;
   }
   ```

6. 在 **方案總管**，開啟捷徑功能表**NorthwindCustomers.svc**檔案，然後選擇**瀏覽器中的檢視**。 Internet Explorer 會開啟，並顯示服務的 XML 結構描述。

7. 由 Internet Explorer 的 [網址] 列複製 URL。

8. 由您在步驟 4 中加入的程式碼中，選取 `http://localhost:53161/NorthwindCustomers.svc/` 並取代為您剛剛複製的 URL。

9. 在功能表列上選擇 **偵錯** > **開始偵錯**執行應用程式。 會顯示客戶資訊。

   現在您會有一個工作應用程式，會顯示來自 NorthwindCustomers 服務的客戶清單。 如果您想要透過服務公開額外的資料，可以將 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 修改為包含來自 Northwind 資料庫的額外資料表。

在下一步的選擇性步驟中，您將了解如何篩選服務所傳回的資料。

## <a name="adding-filtering-capabilities"></a>加入篩選功能
 在此步驟中，您可以自訂要依客戶所在城市篩選資料的應用程式。

### <a name="to-add-filtering-by-city"></a>若要加入根據城市進行篩選的功能

1.  在 **方案總管**，開啟捷徑功能表**Form1.vb**或**Form1.cs**節點，然後選擇 **開啟**。

2.  新增<xref:System.Windows.Forms.TextBox>控制項和<xref:System.Windows.Forms.Button>控制從**工具箱**至表單。

3.  開啟捷徑功能表<xref:System.Windows.Forms.Button>控制項中，選擇**檢視程式碼**，然後新增下列程式碼中的`Button1_Click`事件處理常式：

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4.  在前述的程式碼中，將 `http://localhost:53161/NorthwindCustomers.svc` 取代為 `Form1_Load` 事件處理常式中的 URL。

5.  在功能表列上選擇 **偵錯** > **開始偵錯**執行應用程式。

6.  在 文字 方塊中，輸入**倫敦**，然後選擇  按鈕。 接著，就會只顯示 London 的客戶。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [如何： 加入、 更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)