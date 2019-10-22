---
title: 建立顯示適用于 SharePoint 之 OData 的 Silverlight web 元件
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 859944c51be0abf2e6a326a06a5e4432a69ee4ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655929"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>逐步解說：建立可顯示 SharePoint 之 OData 的 Silverlight web 元件
  SharePoint 2010 會透過 OData 來公開其清單資料。 在 SharePoint 中，OData 服務是由 RESTful 服務 ListData 所執行。 本逐步解說示範如何建立主控 Silverlight 應用程式的 SharePoint web 元件。 Silverlight 應用程式會使用 ListData 來顯示 SharePoint 公告清單資訊。 如需詳細資訊，請參閱[SharePoint FOUNDATION REST 介面](http://go.microsoft.com/fwlink/?LinkId=225999)和[開放式資料通訊協定](http://go.microsoft.com/fwlink/?LinkId=226000)。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 您需要下列元件才能完成此逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式和 Silverlight web 元件
 首先，在 Visual Studio 中建立 Silverlight 應用程式。 Silverlight 應用程式會使用 ListData 服務，從 SharePoint 公告清單中抓取資料。

> [!NOTE]
> 4\.0 之前的 Silverlight 版本都不支援參考 SharePoint 清單資料所需的介面。

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式和 Silverlight web 元件

1. 在功能表列上 **，選擇 [** 檔案]  >  [**新增** > **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [**視覺效果C#**  ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [範本] 窗格中，選擇 [ **SharePoint 2010 Silverlight Web 元件**] 範本。

4. 在 [**名稱**] 方塊中，輸入**SLWebPartTest** ，然後選擇 [**確定]** 按鈕。

    [ **SharePoint 自訂嚮導**] 對話方塊隨即出現。

5. 在 [**指定網站和安全性層級進行偵錯工具**] 頁面上，輸入您要在其中進行網站定義之 SharePoint 伺服器網站的 URL，或使用預設位置（HTTP://<em>系統名稱</em>/）。

6. 在 [**此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [**部署為伺服器陣列方案**] 選項按鈕。

    雖然此範例使用伺服器陣列方案，但 Silverlight web 元件專案可以部署為伺服陣列或沙箱化方案。 如需沙箱化方案和伺服器陣列方案的詳細資訊，請參閱[沙箱化方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 在 [**指定 Silverlight 設定資訊**] 頁面的 [**您要如何關聯 silverlight Web 元件**] 區段中，選擇 [**建立新的 Silverlight 專案並與 Web 元件建立關聯**] 選項按鈕。

8. 將 [**名稱**] 變更為**SLApplication**，將 [**語言**] 設定為**Visual Basic**或**視覺效果C#** ，然後將 [ **silverlight 版本**] 設定為**silverlight 4.0**。

9. 選擇 [**完成]** 按鈕。 專案會顯示在**方案總管**中。

     解決方案包含兩個專案： Silverlight 應用程式和 Silverlight web 元件。 Silverlight 應用程式會從 SharePoint 抓取和顯示清單資料，而 Silverlight web 元件則會主控 Silverlight 應用程式，讓您能夠在 SharePoint 中進行查看。

## <a name="customize-the-silverlight-application"></a>自訂 Silverlight 應用程式
 在 Silverlight 應用程式中新增程式碼和設計項目。

#### <a name="to-customize-the-silverlight-application"></a>自訂 Silverlight 應用程式

1. 在 Silverlight 應用程式中，將元件參考加入至 System.web。 如需詳細資訊，請參閱[如何：使用加入參考對話方塊加入或移除參考](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。

2. 在**方案總管**中，開啟 [**參考**] 的快捷方式功能表，然後選擇 [**加入服務參考**]。

    > [!NOTE]
    > 如果您使用 Visual Basic，則必須選擇**方案總管**頂端的 [**顯示所有**檔案] 圖示，以顯示 [**參考**] 節點。

3. 在 [**加入服務參考**] 對話方塊的 [位址] 方塊中，輸入 SharePoint 網站的 URL （例如 **http://MySPSite** ），然後選擇 [**移至**] 按鈕。

     當 Silverlight 找到 SharePoint OData 服務 ListData 時，它會將位址取代為完整的服務 URL。 在此範例中， http://myserver 會變成 http://myserver/_vti_bin/ListData.svc 。

4. 選擇 [**確定]** 按鈕，將服務參考新增至專案，並使用預設的服務名稱 ServiceReference1。

5. 在功能表列上選擇 [建置] > [建置解決方案]。

6. 根據 SharePoint 服務，將新的資料來源加入至專案。 若要這麼做，請在功能表列上選擇  **View**   > **其他 Windows**  > **資料來源**。

     [**資料來源**] 視窗會顯示所有可用的 SharePoint 清單資料，例如 [工作]、[公告] 和 [行事曆]。

7. 將公告清單資料新增至 Silverlight 應用程式。 您可以從 [**資料來源**] 視窗中，將 [公告] 拖曳至 Silverlight 設計工具。

     這會建立一個系結至 SharePoint 網站之公告清單的方格控制項。

8. 調整格線控制項大小，使其符合 Silverlight 頁面。

9. 在 MainPage 的 xaml Visual Basic 程式碼檔（*MainPage.xaml.cs* for C# Visual 或*MainPage* ）中，加入下列命名空間參考。

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. 在類別的頂端新增下列變數宣告。

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

11. 將 `UserControl_Loaded` 程式取代為下列程式。

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

     請務必以執行 SharePoint 的伺服器名稱取代*ServerName*預留位置。

12. 新增下列錯誤處理常式。

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

## <a name="modify-the-silverlight-web-part"></a>修改 Silverlight web 元件
 變更 Silverlight web 元件專案中的屬性，以啟用 Silverlight 調試。

#### <a name="to-modify-the-silverlight-web-part"></a>修改 Silverlight web 元件

1. 開啟 Silverlight web 元件專案（**SLWebPartTest**）的快捷方式功能表，然後選擇 [**屬性**]。

2. 在 [**屬性**] 視窗中，選擇 [ **SharePoint** ] 索引標籤。

3. 如果尚未選取，請選取 [**啟用 Silverlight 偵錯工具] （而非 [腳本調試**程式]）核取方塊。

4. 儲存專案。

## <a name="test-the-silverlight-web-part"></a>測試 Silverlight web 元件
 在 SharePoint 中測試新的 Silverlight web 元件，以確保它會正確顯示 SharePoint 清單資料。

#### <a name="to-test-the-silverlight-web-part"></a>測試 Silverlight web 元件

1. 選擇**F5**鍵以建立並執行 SharePoint 方案。

2. 在 SharePoint 的 [**網站動作**] 功能表上，選擇 [**新增頁面**]。

3. 在 [**新增頁面**] 對話方塊中，輸入標題，例如 [ **SL Web 元件測試**]，然後選擇 [**建立**] 按鈕。

4. 在頁面設計工具的 [**編輯工具**] 索引標籤上，選擇 [**插入**]。

5. 在索引標籤帶上，選擇 [ **Web 元件**]。

6. 在 [**類別目錄**] 方塊中，選擇 [**自訂**] 資料夾。

7. 在 [ **Web 組件**] 清單中，選擇 Silverlight Web 元件，然後選擇 [**新增**] 按鈕，將 Web 元件新增至設計工具。

8. 將所有新增專案加入您想要的網頁之後，請選擇 [**頁面**] 索引標籤，然後選擇工具列上的 [**儲存 & 關閉**] 按鈕。

     Silverlight web 元件現在應該會顯示來自 SharePoint 網站的公告資料。 根據預設，頁面會儲存在 SharePoint 的 [網站頁面] 清單中。

    > [!NOTE]
    > 在跨網域存取 Silverlight 中的資料時，Silverlight 會防範可用來入侵 web 應用程式的安全性弱點。 如果您在存取 Silverlight 中的遠端資料時遇到問題，請參閱[讓服務可跨網域界限使用](http://go.microsoft.com/fwlink/?LinkId=223276)。

## <a name="see-also"></a>請參閱
- [建立 SharePoint 的 web 元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
