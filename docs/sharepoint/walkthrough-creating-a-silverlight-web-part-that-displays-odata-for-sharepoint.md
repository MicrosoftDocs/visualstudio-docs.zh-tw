---
title: 建立顯示 OData for SharePoint 的 Silverlight web 元件
titleSuffix: ''
description: 建立會顯示適用于 SharePoint 之 OData 的 Silverlight web 元件。 自訂 Silverlight 應用程式，以及修改和測試 Silverlight 網頁元件。
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
ms.topic: how-to
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
ms.openlocfilehash: fdfd510aaea8d09ac20546344f4bbba18bd5f99b
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914786"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>逐步解說：建立顯示適用于 SharePoint 之 OData 的 Silverlight web 元件
  SharePoint 2010 透過 OData 公開其清單資料。 在 SharePoint 中，OData 服務是由 RESTful service ListData 所執行。 本逐步解說將示範如何建立裝載 Silverlight 應用程式的 SharePoint 網頁元件。 Silverlight 應用程式會使用 ListData 來顯示 SharePoint 公告清單資訊。 如需詳細資訊，請參閱 [SharePoint FOUNDATION REST 介面](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) 和 [開放式資料通訊協定](https://www.odata.org/)。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- 支援的 Microsoft Windows 和 SharePoint 版本。

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式和 Silverlight web 元件
 首先，在 Visual Studio 中建立 Silverlight 應用程式。 Silverlight 應用程式會使用 ListData .svc 服務，從 SharePoint 公告清單中取出資料。

> [!NOTE]
> 4.0 之前沒有 Silverlight 版本支援參考 SharePoint 清單資料所需的介面。

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式和 Silverlight web 元件

1. 在功能表列上 **，選擇 [** 檔案  >  **新增**  >  **專案**]，以顯示 [**新增專案**] 對話方塊。

2. 展開 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **SharePoint** ] 節點，然後選擇 [ **2010** ] 節點。

3. 在 [範本] 窗格中，選擇 [ **SharePoint 2010 Silverlight 網頁元件** ] 範本。

4. 在 [ **名稱** ] 方塊中，輸入 **SLWebPartTest** ，然後選擇 [ **確定]** 按鈕。

    [ **SharePoint 自訂嚮導** ] 對話方塊隨即出現。

5. 在 [ **指定偵錯工具的網站和安全性等級** ] 頁面上，輸入您要在其中偵測網站定義的 SharePoint 伺服器網站的 URL，或使用預設位置 (HTTP://<em>系統名稱</em>/) 。

6. 在 [ **此 SharePoint 方案的信任層級為何？** ] 區段中，選擇 [ **部署為伺服器陣列方案** ] 選項按鈕。

    雖然此範例使用伺服器陣列方案，但 Silverlight web 元件專案可以部署為伺服器陣列或沙箱化方案。 如需沙箱化方案與伺服器陣列方案的詳細資訊，請參閱 [沙箱化解決方案考慮](../sharepoint/sandboxed-solution-considerations.md)。

7. 在 [**指定 Silverlight 設定資訊**] 頁面的 [**您要如何建立 silverlight 網頁元件的關聯**] 區段中，選擇 [**建立新的 silverlight 專案]，並將它與 [網頁元件**] 選項按鈕產生關聯。

8. 將 **名稱** 變更為 **SLApplication**、將 **語言** 設定為 **Visual Basic** 或 **Visual c #**，然後將 **silverlight 版本** 設定為 **silverlight 4.0**。

9. 選擇 [完成] 按鈕。 專案會出現在 **方案總管** 中。

     此方案包含兩個專案： Silverlight 應用程式和 Silverlight 網頁元件。 Silverlight 應用程式會從 SharePoint 抓取並顯示清單資料，而 Silverlight web 元件會裝載 Silverlight 應用程式，讓您可以在 SharePoint 中加以查看。

## <a name="customize-the-silverlight-application"></a>自訂 Silverlight 應用程式
 在 Silverlight 應用程式中加入程式碼和設計項目。

#### <a name="to-customize-the-silverlight-application"></a>自訂 Silverlight 應用程式

1. 在 Silverlight 應用程式中，將元件參考加入至 System.object。 如需詳細資訊，請參閱 [如何：使用加入參考對話方塊加入或移除參考](/previous-versions/wkze6zky(v=vs.140))。

2. 在 **方案總管** 中，開啟 [ **參考**] 的快捷方式功能表，然後選擇 [ **加入服務參考**]。

    > [!NOTE]
    > 如果您是使用 Visual Basic，則必須選擇 **方案總管** 頂端的 [**顯示所有** 檔案] 圖示，以顯示 [**參考**] 節點。

3. 在 [ **加入服務參考** ] 對話方塊的 [位址] 方塊中，輸入 SharePoint 網站的 URL （例如），然後 **http://MySPSite** 選擇 [ **移至** ] 按鈕。

     當 Silverlight 找出 SharePoint OData 服務 ListData 時，它會將位址取代為完整的服務 URL。 在此範例中， http://myserver 會變成 http://myserver/_vti_bin/ListData.svc 。

4. 選擇 [ **確定]** 按鈕，將服務參考加入至專案，並使用預設服務名稱 ServiceReference1。

5. 在功能表列上，選擇 [**組建**  >  **組建方案**]。

6. 根據 SharePoint 服務，將新的資料來源加入至專案。 若要這樣做，請在功能表列上選擇 [ **View**  >  **Other Windows**  >  **資料來源**]。

     [ **資料來源** ] 視窗會顯示所有可用的 SharePoint 清單資料，例如工作、公告和行事曆。

7. 將公告清單資料新增至 Silverlight 應用程式。 您可以從 [ **資料來源** ] 視窗中，將 [公告] 拖曳至 Silverlight 設計工具。

     這會建立一個系結至 SharePoint 網站之公告清單的方格控制項。

8. 調整方格控制項的大小，使其符合 Silverlight 頁面。

9. 在 MainPage 的 MainPage.xaml.cs 中， (Visual c # 或) Visual Basic *MainPage* 的 *MainPage.xaml.cs* ，請新增下列命名空間參考。

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

10. 在類別的最上方新增下列變數宣告。

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

11. 將程式取代為 `UserControl_Loaded` 下列程式。

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

     請務必以執行 SharePoint 的伺服器名稱取代 *ServerName* 預留位置。

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

## <a name="modify-the-silverlight-web-part"></a>修改 Silverlight 網頁元件
 變更 Silverlight web 元件專案中的屬性，以啟用 Silverlight 調試。

#### <a name="to-modify-the-silverlight-web-part"></a>修改 Silverlight 網頁元件

1. 開啟 Silverlight web 元件專案 (**SLWebPartTest**) 的快捷方式功能表，然後選擇 [ **屬性**]。

2. 在 [ **屬性** ] 視窗中，選擇 [ **SharePoint** ] 索引標籤。

3. 如果尚未選取，請選取 [ **啟用 Silverlight 偵錯工具 (而非腳本偵錯工具)** ] 核取方塊。

4. 儲存專案。

## <a name="test-the-silverlight-web-part"></a>測試 Silverlight 網頁元件
 在 SharePoint 中測試新的 Silverlight web 元件，以確保它會正確地顯示 SharePoint 清單資料。

#### <a name="to-test-the-silverlight-web-part"></a>測試 Silverlight 網頁元件

1. 選擇 **F5** 鍵來建立和執行 SharePoint 方案。

2. 在 SharePoint 的 [ **網站動作** ] 功能表上，選擇 [ **新增頁面**]。

3. 在 [ **新增頁面** ] 對話方塊中，輸入標題，例如 [ **SL Web Part Test**]，然後選擇 [ **建立** ] 按鈕。

4. 在 [頁面設計工具] 的 [ **編輯工具** ] 索引標籤上，選擇 [ **插入**]。

5. 在索引標籤帶上，選擇 [ **Web 元件**]。

6. 在 [ **類別** ] 方塊中，選擇 [ **自訂** ] 資料夾。

7. 在 **Web 組件** 清單中，選擇 Silverlight 網頁元件，然後選擇 [ **加入** ] 按鈕，將 Web 元件加入至設計工具。

8. 當您將所有新增專案加入至您想要的網頁之後，請選擇 [ **頁面** ] 索引標籤，然後選擇工具列上的 [ **儲存 & 關閉** ] 按鈕。

     Silverlight 網頁元件現在應該會顯示來自 SharePoint 網站的公告資料。 根據預設，頁面會儲存在 SharePoint 的 [網站] 頁面清單中。

    > [!NOTE]
    > 在跨網域存取 Silverlight 中的資料時，Silverlight 會防範可用於惡意探索 web 應用程式的安全性弱點。 如果您在 Silverlight 中存取遠端資料時遇到問題，請參閱 [讓服務可跨網域界限使用](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95))。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [部署、發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)