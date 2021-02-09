---
title: 使用 WPF & 建立 WCF 資料服務 Entity Framework
description: 使用 WPF 和 Entity Framework 建立 WCF 資料服務，該服務裝載于 ASP.NET web 應用程式中，然後從 Windows Forms 應用程式存取。
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 54699947588e29da7312c0574833a13bbc3c8cfd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858185"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>逐步解說︰使用 WPF 和 Entity Framework 建立 WCF 資料服務
在本逐步解說中，會示範如何建立裝載於 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的簡單 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，並從 Windows Forms 應用程式存取此服務。

在這個逐步解說中，您會：

- 建立裝載 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] 的 Web 應用程式。

- 建立 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 代表 `Customers` Northwind 資料庫中資料表的。

- 建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]。

- 建立用戶端應用程式，並加入 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]的參考。

- 啟用對服務的資料繫結，並產生使用者介面。

- 您可以選擇在應用程式中加入篩選功能。

## <a name="prerequisites"></a>必要條件
本逐步解說使用 SQL Server Express LocalDB 和 Northwind 範例資料庫。

1. 如果您沒有 LocalDB SQL Server Express，請從 [SQL Server Express 下載頁面](https://www.microsoft.com/sql-server/sql-server-editions-express)或透過 **Visual Studio 安裝程式** 進行安裝。 在 **Visual Studio 安裝程式** 中，您可以安裝 SQL Server Express LocalDB 作為 **資料儲存和處理** 工作負載的一部分，或安裝為個別的元件。

2. 遵循下列步驟來安裝 Northwind 範例資料庫：

    1. 在 Visual Studio 中，開啟 [ **SQL Server 物件總管** ] 視窗。  (**SQL Server 物件總管** 會安裝為 Visual Studio 安裝程式中 **資料儲存和處理** 工作負載的一部分。 ) 展開 **SQL Server** 節點。 以滑鼠右鍵按一下您的 LocalDB 實例，然後選取 [追加 **查詢**]。

       [查詢編輯器] 視窗隨即開啟。

    2. 將 [Northwind transact-sql 腳本](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 複製到剪貼簿。 此 T-sql 腳本會從頭開始建立 Northwind 資料庫，並在其中填入資料。

    3. 將 T-sql 腳本貼入 [查詢編輯器]，然後選擇 [ **執行** ] 按鈕。

       經過一小段時間之後，查詢就會完成執行，並建立 Northwind 資料庫。

## <a name="creating-the-service"></a>建立服務
若要建立 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]，請新增 Web 專案、建立 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]，然後從模型建立服務。

在第一個步驟中，您會加入 Web 專案來裝載服務。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>建立 Web 專案

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]。

2. 展開 [新增專案] 對話方塊中的 [Visual Basic] 或 [Visual C#] 和 [Web] 節點，然後選擇 [ASP.NET Web 應用程式] 範本。

3. 在 [名稱] 文字方塊中，輸入 **NorthwindWeb**，然後選擇 [確定] 按鈕。

4. 在 [新增 ASP.NET 專案] 對話方塊的 [選取範本] 清單中，選擇 [空白]，然後選擇 [確定] 按鈕。

在下一個步驟中，您會建立 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 代表 `Customers` Northwind 資料庫中資料表的。

### <a name="to-create-the-entity-data-model"></a>若要建立實體資料模型

1. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

2. 在 [新增新項目] 對話方塊中，選擇 [資料] 節點，然後選擇 [ADO.NET 實體資料模型] 項目。

3. 在 [ **名稱** ] 文字方塊中，輸入 `NorthwindModel` ，然後選擇 [ **加入** ] 按鈕。

     [實體資料模型精靈] 隨即出現。

4. 在實體資料模型精靈的 [選擇模型內容] 頁面上，選擇 [來自資料庫的 EF 設計工具] 項目，然後選擇 [下一步] 按鈕。

5. 在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：

    - 如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選擇這個資料連接。

         -或-

    - 選擇 [新增連線] 按鈕，設定新的資料連線。 如需詳細資訊，請參閱 [加入新的連接](../data-tools/add-new-connections.md)。

6. 如果資料庫需要密碼，請選擇 [是，在連接字串中包含敏感性資料] 選項按鈕，然後選擇 [下一步] 按鈕。

    > [!NOTE]
    > 如果對話方塊隨即出現，請選擇 [是]，將檔案儲存到您的專案。

7. 在 [選擇您的版本] 頁面上，選擇 [Entity Framework 5.0] 選項按鈕，然後選擇 [下一步] 按鈕。

    > [!NOTE]
    > 若要使用最新版的 Entity Framework 6 與 WCF 服務，您還需要安裝 WCF Data Services Entity Framework Provider NuGet 套件。 請參閱 [使用 WCF Data Services 5.6.0 搭配 Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/)。

8. 展開 [選擇您的資料庫物件] 頁面上的 [資料表] 節點，選取 [客戶] 核取方塊，然後選擇 [完成] 按鈕。

     實體模型圖表會隨即顯示，並將 *NorthwindModel .edmx* 檔加入至您的專案。

在下一個步驟中，您會建立並測試資料服務。

### <a name="to-create-the-data-service"></a>若要建立資料服務

1. 在功能表列上，選擇 [ **Project**  >  **加入新專案**]。

2. 在 [新增新項目] 對話方塊中，選擇 [Web] 節點，然後選擇 **WCF Data Service 5.6** 項目。

3. 在 [ **名稱** ] 文字方塊中，輸入 `NorthwindCustomers` ，然後選擇 [ **加入** ] 按鈕。

     **NorthwindCustomers.svc** 檔案會出現在 [程式碼編輯器] 中。

4. 在 [程式碼編輯器] 中找出第一個 `TODO:` 註解，並以下列程式碼取代：

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. 將 `InitializeService` 事件處理常式中的註解以下列程式碼取代：

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. 在功能表列上，選擇 [ **Debug**  >  **啟動但不進行調試**] 來執行服務。 瀏覽器視窗隨即開啟，並顯示服務的 XML 架構。

7. 在 **網址** 列中，輸入 `Customers` **NorthwindCustomers** 的 URL 結尾，然後選擇 **enter** 鍵。

     資料表中資料的 XML 標記法 `Customers` 隨即出現。

    > [!NOTE]
    > 在某些情況中，Internet Explorer 會將資料錯譯為 RSS 摘要 (RSS Feed)。 您必須確定顯示 RSS 摘要的選項已停用。 如需詳細資訊，請參閱[針對服務參考進行疑難排解](../data-tools/troubleshooting-service-references.md)。

8. 關閉瀏覽器視窗。

在接下來的步驟中，您會建立 Windows Forms 用戶端應用程式以取用服務。

## <a name="creating-the-client-application"></a>建立用戶端應用程式
若要建立用戶端應用程式，請新增第二個專案、將服務參考新增至專案、設定資料來源，並建立使用者介面來顯示服務中的資料。

在第一個步驟中，您會將 Windows Forms 專案加入至方案，並將其設定為啟始專案。

### <a name="to-create-the-client-application"></a>若要建立用戶端應用程式

1. 在功能表列上，選擇 [檔案]、[**加入**  >  **新專案**]。

2. 在 [ **新增專案** ] 對話方塊中，展開 [ **Visual Basic** ] 或 [ **Visual c #** ] 節點，選擇 [ **Windows** ] 節點，然後選擇 [ **Windows Forms 應用程式**]。

3. 在 [名稱] 文字方塊中，輸入 `NorthwindClient`，然後選擇 [確定] 按鈕。

4. 在 [方案總管] 中，選擇 [NorthwindClient] 專案節點。

5. 在功能表列上，選擇 [專案]、[設定為啟始專案]。

在下一個步驟中，您會將服務參考加入至 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Web 專案中的。

### <a name="to-add-a-service-reference"></a>若要加入服務參考

1. 在功能表列上，選擇 [ **Project**  >  **加入服務參考**]。

2. 選擇 [新增服務參考] 對話方塊中的 [探索] 按鈕。

     NorthwindCustomers 服務的 URL 會隨即顯示在 [位址] 欄位中。

3. 選擇 [確定] 按鈕以新增服務參考。

在下一個步驟中，您會設定資料來源，以啟用服務的資料系結。

### <a name="to-enable-data-binding-to-the-service"></a>若要啟用對服務的資料繫結

1. 在功能表列上，選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

   [資料來源] 視窗隨即開啟。

2. 在 [資料來源] 視窗中，選擇 [新增新資料來源] 按鈕。

3. 在 [資料來源組態精靈] 的 [選擇資料來源類型] 頁面中，選擇 [物件]，然後選擇 [下一步] 按鈕。

4. 展開 [選取資料物件] 頁面上的 [NorthwindClient] 節點，然後展開 [NorthwindClient.ServiceReference1] 節點。

5. 選取 [客戶] 核取方塊，然後選擇 [完成] 按鈕。

在下一個步驟中，您會建立使用者介面來顯示服務中的資料。

### <a name="to-create-the-user-interface"></a>若要建立使用者介面

1. 在 [資料來源] 視窗中，開啟 [客戶] 節點的捷徑功能表，然後選擇 [複製]。

2. 在 [Form1.vb] 或 [Form1.cs] 表單設計工具中，開啟捷徑功能表並選擇 [貼上]。

    表單中會加入一個 <xref:System.Windows.Forms.DataGridView> 控制項、一個 <xref:System.Windows.Forms.BindingSource> 元件，和一個 <xref:System.Windows.Forms.BindingNavigator> 元件。

3. 選擇 [CustomersDataGridView] 控制項，然後在 [屬性] 視窗中，將 [Dock] 屬性設為 [填滿]。

4. 在 **方案總管** 中，開啟 [ **Form1** ] 節點的快捷方式功能表，然後選擇 [ **View Code** ] 以開啟程式碼編輯器，並在檔案頂端新增下列 `Imports` 或 `Using` 語句：

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

6. 在 [方案總管] 中，開啟 **NorthwindCustomers.svc** 檔案的捷徑功能表，然後選擇 [在瀏覽器中檢視]。 Internet Explorer 隨即開啟，並顯示服務的 XML 架構。

7. 由 Internet Explorer 的 [網址] 列複製 URL。

8. 由您在步驟 4 中加入的程式碼中，選取 `http://localhost:53161/NorthwindCustomers.svc/` 並取代為您剛剛複製的 URL。

9. 在功能表列上，選擇 [ **Debug**  >  **開始調試** 程式] 以執行應用程式。 會顯示客戶資訊。

   現在您會有一個工作應用程式，會顯示來自 NorthwindCustomers 服務的客戶清單。 如果您想要透過服務公開額外的資料，可以將 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 修改為包含來自 Northwind 資料庫的額外資料表。

在下一個選擇性步驟中，您將瞭解如何篩選服務所傳回的資料。

## <a name="adding-filtering-capabilities"></a>加入篩選功能
在此步驟中，您會自訂應用程式，以依客戶的城市篩選資料。

### <a name="to-add-filtering-by-city"></a>若要加入根據城市進行篩選的功能

1. 在 [方案總管] 中，開啟 [Form1.vb] 或 [Form1.cs] 節點的捷徑功能表，然後選擇 [開啟]。

2. 從 [工具箱] 將 <xref:System.Windows.Forms.TextBox> 控制項和 <xref:System.Windows.Forms.Button> 控制項新增至表單。

3. 開啟控制項的快捷方式功能表 <xref:System.Windows.Forms.Button> ，選擇 [ **View Code**]，然後在事件處理常式中加入下列程式碼 `Button1_Click` ：

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

4. 在前述的程式碼中，將 `http://localhost:53161/NorthwindCustomers.svc` 取代為 `Form1_Load` 事件處理常式中的 URL。

5. 在功能表列上，選擇 [ **Debug**  >  **開始調試** 程式] 以執行應用程式。

6. 在文字方塊中輸入 **London**，然後選擇該按鈕。 接著，就會只顯示 London 的客戶。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [如何：加入、更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
