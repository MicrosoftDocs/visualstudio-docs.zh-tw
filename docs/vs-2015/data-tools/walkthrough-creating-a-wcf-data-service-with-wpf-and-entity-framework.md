---
title: 逐步解說： 使用 WPF 和 Entity Framework 建立 WCF 資料服務 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3d115c7ea7b2739f49492fb28fe855e2638d972c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889590"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>逐步解說： 使用 WPF 和 Entity Framework 建立 WCF 資料服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
本逐步解說示範如何建立簡單[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]裝載在[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Web 應用程式，然後將它存取 Windows Form 應用程式。  
  
 在這份逐步解說中，您將能夠：  
  
-   建立裝載 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]的 Web 應用程式。  
  
-   建立呈現 Northwind 資料庫中的 Customers 資料表的 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]。  
  
-   建立 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]。  
  
-   建立用戶端應用程式，並加入 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]的參考。  
  
-   啟用對服務的資料繫結，並產生使用者介面。  
  
-   您可以選擇在應用程式中加入篩選功能。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Northwind 範例資料庫。  
  
     如果您的開發電腦上沒有這個資料庫，則可以從 [Microsoft 下載中心](http://go.microsoft.com/fwlink/?LinkID=98088)下載。 如需相關指示，請參閱 <<c0> [ 下載範例資料庫](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5)。  
  
## <a name="creating-the-service"></a>建立服務  
 若要建立 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]，請加入 Web 專案、建立 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]，然後透過模型建立服務。  
  
 在第一個步驟中，您要加入一個 Web 專案以裝載服務。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>若要建立 Web 專案  
  
1. 在功能表列上選擇 **檔案**，**新增**，**專案**。  
  
2. 在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#** 和**Web**節點，然後選擇  **ASP.NET Web 應用程式**範本。  
  
3. 在 [**名稱**文字方塊中，輸入**NorthwindWeb**，然後選擇 **[確定]** ] 按鈕。  
  
4. 中**新增 ASP.NET 專案**對話方塊中，於**選取範本**清單中，選擇**空**，然後選擇 **[確定]** 按鈕。  
  
   在此步驟中，您會建立一個呈現 Northwind 資料庫中 Customers 資料表的 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]。  
  
#### <a name="to-create-the-entity-data-model"></a>若要建立實體資料模型  
  
1. 在功能表列上選擇 **專案**，**加入新項目**。  
  
2. 在**加入新項目**對話方塊方塊中，選擇**資料**節點，然後選擇**ADO.NET 實體資料模型**項目。  
  
3. 在 **名稱**文字方塊中，輸入`NorthwindModel`，然後選擇**新增**按鈕。  
  
    [實體資料模型精靈] 隨即出現。  
  
4. 在 [實體資料模型精靈] 中，在**選擇模型內容**頁面上，選擇**資料庫的 EF Designer**項目，然後再選擇 [**下一步]** 按鈕。  
  
5. 在 [ **選擇資料連接** ] 頁面上，執行下列其中一個步驟：  
  
   -   如果下拉式清單中有提供 Northwind 範例資料庫的資料連接，請選擇這個資料連接。  
  
        -或-  
  
   -   選擇**新的連接**，設定新的資料連接 按鈕。 如需詳細資訊，請參閱 <<c0> [ 新增連線](../data-tools/add-new-connections.md)。  
  
6. 如果資料庫需要密碼，請選擇**是，連接字串中包括敏感性資料**選項按鈕，然後再選擇**下一步**  按鈕。  
  
   > [!NOTE]
   >  如果出現對話方塊，請選擇**是**將檔案儲存至您的專案。  
  
7. 在 **選擇您的版本**頁面上，選擇**Entity Framework 5.0**選項按鈕，然後選擇**下一步**  按鈕。  
  
   > [!NOTE]
   >  除了使用最新版的 Entity Framework 6 與 WCF 服務之外，您還需要安裝 WCF Data Services Entity Framework Provider NuGet 套件。 請參閱[使用 WCF Data Services 5.6.0 和 Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx)。  
  
8. 在上**選擇您的資料庫物件**頁面上，展開**資料表**節點中，選取**客戶**核取方塊，，然後選擇**完成**按鈕。  
  
    實體模型圖表隨即顯示，並將 NorthwindModel.edmx 檔案加入至您的專案中。  
  
   在這個步驟中，您將會建立與測試資料服務。  
  
#### <a name="to-create-the-data-service"></a>若要建立資料服務  
  
1. 在功能表列上選擇 **專案**，**加入新項目**。  
  
2. 在**加入新項目**對話方塊方塊中，選擇**Web**節點，然後選擇**WCF Data Service 5.6**項目。  
  
3. 在 **名稱**文字方塊中，輸入`NorthwindCustomers`，然後選擇**新增**按鈕。  
  
    NorthwindCustomers.svc 檔案會出現在**程式碼編輯器**。  
  
4. 在 **程式碼編輯器**，找出第一個`TODO:`註解，並以下列程式碼取代：  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. 將 `InitializeService` 事件處理常式中的註解以下列程式碼取代：  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. 在功能表列上選擇 **偵錯**，**啟動但不偵錯**來執行服務。 瀏覽器視窗隨即開啟，並顯示服務的 XML 結構描述。  
  
7. 中**地址**列上，輸入`Customers`northwindcustomers.svc，URL 結尾處，然後選擇**ENTER**索引鍵。  
  
    隨即會顯示 Customers 資料表中資料的 XML 表示。  
  
   > [!NOTE]
   >  在某些情況中，Internet Explorer 會將資料錯譯為 RSS 摘要 (RSS Feed)。 您必須確定顯示 RSS 摘要的選項已停用。 如需詳細資訊，請參閱 <<c0> [ 疑難排解服務參考](../data-tools/troubleshooting-service-references.md)。  
  
8. 關閉瀏覽器視窗。  
  
   在接下來的步驟中，您將要建立 Windows Form 用戶端應用程式以使用服務。  
  
## <a name="creating-the-client-application"></a>建立用戶端應用程式  
 若要建立用戶端應用程式，您將要加入第二個專案、在專案中加入服務參考、設定資料來源，並建立要顯示來自服務之資料的使用者介面。  
  
 在第一個步驟中，您要在方案中加入 Windows Form 專案，並設定為啟始專案。  
  
#### <a name="to-create-the-client-application"></a>若要建立用戶端應用程式  
  
1. 在功能表列上選擇 [檔案]**新增**，**新的專案**。  
  
2. 在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#** 節點，然後選擇  **Windows**  節點，然後選擇  **Windows Forms 應用程式**。  
  
3. 在 [名稱] 文字方塊中，輸入 `NorthwindClient`，然後選擇 [確定] 按鈕。  
  
4. 在 **方案總管**，選擇**NorthwindClient**專案節點。  
  
5. 在功能表列上選擇 **專案**，**設定為啟始專案**。  
  
   在這個步驟中，您將在 Web 專案中加入 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]的服務參考。  
  
#### <a name="to-add-a-service-reference"></a>若要加入服務參考  
  
1. 在功能表列上選擇 **專案**，**加入服務參考**。  
  
2. 在 [**加入服務參考**對話方塊方塊中，選擇**Discover** ] 按鈕。  
  
    NorthwindCustomers 服務的 URL 會出現在**地址**欄位。  
  
3. 選擇**確定**按鈕以新增服務參考。  
  
   在這個步驟中，您將設定資料來源，讓資料能夠繫結至服務。  
  
#### <a name="to-enable-data-binding-to-the-service"></a>若要啟用對服務的資料繫結  
  
1. 在功能表列上選擇 **檢視**，**其他 Windows**， **Zdroje dat**。  
  
2. 在 **資料來源** 視窗中，選擇**加入新的資料來源** 按鈕。  
  
3. 上**選擇資料來源類型**頁面**資料來源組態精靈**，選擇**物件**，然後選擇**下一步**按鈕.  
  
4. 在上**選取資料物件**頁面上，展開**NorthwindClient**節點，然後展開**NorthwindClient.ServiceReference1**節點。  
  
5. 選取 [**客戶**核取方塊，然後再選擇**完成**] 按鈕。  
  
   在這個步驟中，您將會建立要顯示來自服務之資料的使用者介面。  
  
#### <a name="to-create-the-user-interface"></a>若要建立使用者介面  
  
1. 在 **資料來源** 視窗中，開啟捷徑功能表**客戶**節點，然後選擇 **複製**。  
  
2. 在  **Form1.vb**或是**Form1.cs**表單設計工具，開啟捷徑功能表，然後選擇**貼上**。  
  
    表單中會加入一個 <xref:System.Windows.Forms.DataGridView> 控制項、一個 <xref:System.Windows.Forms.BindingSource> 元件，和一個 <xref:System.Windows.Forms.BindingNavigator> 元件。  
  
3. 選擇**CustomersDataGridView**控制項，然後在**屬性** 視窗中設定**停駐**屬性設**填滿**。  
  
4. 在**方案總管**，開啟捷徑功能表**Form1**節點，然後選擇 **檢視程式碼**開啟程式碼編輯器，並加入下列 Imports 或 Using 陳述式檔案的頂端：  
  
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
  
6. 在 **方案總管**，開啟 NorthwindCustomers.svc 檔案的捷徑功能表，然後選擇**瀏覽器中的檢視**。 Internet Explorer 隨即開啟，並顯示服務的 XML 結構描述。  
  
7. 由 Internet Explorer 的 [網址] 列複製 URL。  
  
8. 由您在步驟 4 中加入的程式碼中，選取 `http://localhost:53161/NorthwindCustomers.svc/` 並取代為您剛剛複製的 URL。  
  
9. 在功能表列上選擇 **偵錯**，**開始偵錯**執行應用程式。 客戶資訊隨即顯示。  
  
   現在您會有一個工作應用程式，會顯示來自 NorthwindCustomers 服務的客戶清單。 如果您想要透過服務公開額外的資料，可以將 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 修改為包含來自 Northwind 資料庫的額外資料表。  
  
   在下一個選擇性的步驟中，您將會學習如何篩選服務傳回的資料。  
  
## <a name="adding-filtering-capabilities"></a>加入篩選功能  
 在此步驟中，您將會自訂應用程式，根據客戶的所在城市篩選資料。  
  
#### <a name="to-add-filtering-by-city"></a>若要加入根據城市進行篩選的功能  
  
1.  在 **方案總管**，開啟捷徑功能表**Form1.vb**或**Form1.cs**節點，然後選擇 **開啟**。  
  
2.  新增<xref:System.Windows.Forms.TextBox>控制項和<xref:System.Windows.Forms.Button>控制從**工具箱**至表單。  
  
3.  開啟捷徑功能表<xref:System.Windows.Forms.Button>控制項，並選擇**檢視程式碼**，然後新增下列程式碼中的`Button1_Click`事件處理常式：  
  
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
  
5.  在功能表列上選擇 **偵錯**，**開始偵錯**執行應用程式。  
  
6.  在 文字 方塊中，輸入**倫敦**，然後選擇  按鈕。 接著，就會只顯示 London 的客戶。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Communication Foundation 服務和 Visual Studio 中的 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [如何：新增、更新或移除 WCF 資料服務參考](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)

