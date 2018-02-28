---
title: "逐步解說： 建立 Silverlight Web 組件會顯示 for SharePoint 的 OData |Microsoft 文件"
ms.custom: 
ms.date: 02/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 3c2c66490e0eb46508fce0f346fe44563548b407
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight Web 組件
  SharePoint 2010 會透過 OData 公開其清單資料。 在 SharePoint 中，OData 服務是服務所實作的 RESTful ListData.svc。 本逐步解說示範如何建立裝載 Silverlight 應用程式的 SharePoint web 組件。 Silverlight 應用程式會使用 ListData.svc 顯示 SharePoint 公告清單資訊。 如需詳細資訊，請參閱[SharePoint Foundation REST 介面](http://go.microsoft.com/fwlink/?LinkId=225999)和[開放式資料通訊協定](http://go.microsoft.com/fwlink/?LinkId=226000)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   支援的 Microsoft Windows 和 SharePoint 版本。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="creating-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式與 Silverlight Web 組件  
 首先，在 Visual Studio 中建立的 Silverlight 應用程式。 Silverlight 應用程式會使用 ListData.svc 服務從 SharePoint 宣告清單中擷取資料。  
  
> [!NOTE]  
>  不到 Silverlight 4.0 之前的版本支援所需的介面參考 SharePoint 清單資料。  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>若要建立的 Silverlight 應用程式和 Silverlight web 組件  
  
1.  在功能表列上選擇 [**檔案**，**新增**，**專案**顯示**新專案**] 對話方塊。  
  
2.  展開**SharePoint**節點之下**Visual C#**或**Visual Basic**，然後選擇  **2010年**節點。  
  
3.  在 範本 窗格中，選擇  **SharePoint 2010 Silverlight Web 組件**範本。  
  
4.  在**名稱**方塊中，輸入**SLWebPartTest** ，然後選擇 [**確定**] 按鈕。  
  
     **SharePoint 自訂精靈** 對話方塊隨即出現。  
  
5.  在**指定偵錯的網站和安全性層級**頁面上，輸入您要偵錯網站定義中，SharePoint 伺服器網站的 URL，或使用預設位置 (http://*系統名稱*/).  
  
6.  在**此 SharePoint 方案的信任層級為何？**區段中，選擇**部署為伺服陣列方案**選項按鈕。  
  
     雖然這個範例會使用伺服器陣列方案，Silverlight web 組件專案可以部署為伺服陣列或沙箱化方案。 如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。  
  
7.  在**您要如何關聯 Silverlight Web 組件**區段**指定 Silverlight 組態資訊**頁面上，選擇**建立新的 Silverlight 專案，關聯 web 組件**選項按鈕。  
  
8.  變更**名稱**至**SLApplication**，將**語言**為**Visual Basic**或**Visual C#**，然後設定**Silverlight 版本**至**Silverlight 4.0**。  
  
9. 選擇**完成** 按鈕。 中會出現專案**方案總管 中**。  
  
     方案包含兩個專案： 將 Silverlight 應用程式和 Silverlight web 組件。 Silverlight 應用程式會擷取並顯示從 SharePoint 清單資料和 Silverlight web 組件裝載 Silverlight 應用程式，讓您在 SharePoint 中檢視它。  
  
##  <a name="customizing-the-silverlight-application"></a>自訂 Silverlight 應用程式  
 新增 Silverlight 應用程式程式碼和設計的項目。  
  
#### <a name="to-customize-the-silverlight-application"></a>若要自訂 Silverlight 應用程式  
  
1.  加入 System.Windows.Data 的組件參考的 Silverlight 應用程式中。 如需詳細資訊，請參閱[如何： 加入或移除參考使用加入參考對話方塊](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
2.  在**方案總管] 中**，開啟捷徑功能表**參考**，然後選擇 [**加入服務參考**。  
  
    > [!NOTE]  
    >  如果您使用 Visual Basic，您必須選擇**顯示所有檔案**上方的圖示**方案總管 中**顯示**參考**節點。  
  
3.  在網址方塊中的**加入服務參考**對話方塊方塊中，輸入您的 SharePoint 網站的 URL，例如**http://MySPSite**，然後選擇 [**移**] 按鈕。  
  
     當 Silverlight 找出 SharePoint OData 服務 ListData.svc 時，它會取代位址的完整服務 URL。 例如，http://myserver 會變成 http://myserver/_vti_bin/ListData.svc。  
  
4.  選擇**確定**; 按鈕以加入服務參考加入專案，並使用預設服務名稱 ServiceReference1。  
  
5.  在功能表列上，選擇 [建置] 、[建置方案] 。  
  
6.  將新的資料來源加入至 SharePoint 服務為基礎的專案。 若要這樣做，請在功能表列上選擇 **檢視**，**其他視窗**，**資料來源**。  
  
     **資料來源** 視窗會顯示所有可用的 SharePoint 清單資料，例如工作、 公告及行事曆。  
  
7.  新增 Silverlight 應用程式的公告清單資料。 您可以將 「 宣告 」 從**資料來源**視窗拖曳至 Silverlight designer。  
  
     這會建立方格控制項繫結至 SharePoint 網站的公告清單。  
  
8.  調整大小以符合 Silverlight 頁面的方格控制項。  
  
9. 在 MainPage.xaml 的程式碼檔案中 (MainPage.xaml.cs Visual C#) 或 MainPage.xaml.vb Visual basic 中，加入下列命名空間參考。  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. 類別的最上方加入下列變數宣告。  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
   
11. 取代`UserControl_Loaded`使用下列程序。  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
     請務必取代*ServerName*您執行 SharePoint 的伺服器名稱的預留位置。  
  
12. 加入下列的錯誤處理程序。  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
       
## <a name="modifying-the-silverlight-web-part"></a>修改 Silverlight Web 組件  
 變更在啟用 Silverlight 偵錯的 Silverlight web 組件專案屬性。  
  
#### <a name="to-modify-the-silverlight-web-part"></a>若要修改 Silverlight web 組件  
  
1.  開啟 Silverlight web 組件專案的捷徑功能表 (**SLWebPartTest**)，然後選擇 **屬性**。  
  
2.  在**屬性**視窗中，選擇**SharePoint**  索引標籤。  
  
3.  如果尚未選取，請選取**啟用 Silverlight 偵錯 （而不指令碼偵錯）**核取方塊。  
  
4.  儲存專案。  
  
##  <a name="testing-the-silverlight-web-part"></a>測試 Silverlight Web 組件  
 測試新的 Silverlight web 組件在 SharePoint，以確保它正確顯示 SharePoint 清單資料。  
  
#### <a name="to-test-the-silverlight-web-part"></a>若要測試 Silverlight web 組件  
  
1.  選擇 F5 鍵建置並執行 SharePoint 方案。  
  
2.  在 SharePoint 中，在**網站動作**功能表上，選擇**新頁面**。  
  
3.  在**新頁面** 對話方塊中，輸入標題，例如**SL Web 組件測試**，然後選擇 **建立** 按鈕。  
  
4.  在網頁設計工具上**編輯工具**索引標籤上，選擇**插入**。  
  
5.  在索引標籤區域中，選擇  **Web 組件**。  
  
6.  在**類別**方塊中，選擇**自訂**資料夾。  
  
7.  在**Web 組件**清單中，選擇 Silverlight web 組件，然後選擇 **新增**按鈕，將 web 組件加入至設計工具。  
  
8.  您對所有新增的項目您想要的網頁之後，請選擇**頁面**索引標籤，然後選擇 **儲存並關閉**工具列上的按鈕。  
  
     Silverlight web 組件應該立即顯示宣告中資料的 SharePoint 網站。 根據預設，頁面會儲存在 SharePoint 中的網站頁面清單。  
  
    > [!NOTE]  
    >  存取資料時在 Silverlight 中跨網域，Silverlight 會防範可用來利用 web 應用程式的安全性弱點。 如果您在存取 Silverlight 中的遠端資料時遇到問題，請參閱[讓服務提供跨網域界限](http://go.microsoft.com/fwlink/?LinkId=223276)。  
  
## <a name="see-also"></a>請參閱  
 [建立 SharePoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  
