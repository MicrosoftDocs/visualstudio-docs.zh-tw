---
title: 逐步解說：建立 Silverlight Web 組件可顯示 SharePoint 之 OData |Microsoft Docs
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
ms.openlocfilehash: ee8e4b412422d6f385e39f4fdbf44e151313c0a2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605116"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>逐步解說：建立顯示 SharePoint 之 OData 的 Silverlight web 組件
  SharePoint 2010 會透過 OData 公開其清單資料。 在 SharePoint 中，OData 服務是 RESTful 服務 ListData.svc 所實作。 本逐步解說示範如何建立裝載 Silverlight 應用程式的 SharePoint web 組件。 Silverlight 應用程式會顯示使用 ListData.svc 公告 SharePoint 清單資訊。 如需詳細資訊，請參閱 < [SharePoint Foundation REST 介面](http://go.microsoft.com/fwlink/?LinkId=225999)並[開放式資料通訊協定](http://go.microsoft.com/fwlink/?LinkId=226000)。

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   支援的 Microsoft Windows 和 SharePoint 版本。

-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>建立 Silverlight 應用程式和 Silverlight web 組件
 首先，在 Visual Studio 中建立 Silverlight 應用程式。 Silverlight 應用程式使用 ListData.svc 服務，從 SharePoint 宣告清單擷取資料。

> [!NOTE]
>  任何版本的 Silverlight 4.0 之前不支援所需的介面參考 SharePoint 清單資料。

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>若要建立 Silverlight 應用程式和 Silverlight web 組件

1. 在功能表列上選擇 [**檔案** > **新增** > **專案**顯示**新專案**] 對話方塊。

2. 依序展開**SharePoint**節點之下**Visual C#** 或**Visual Basic**，然後選擇**2010年**節點。

3. 在 [範本] 窗格中，選擇**SharePoint 2010 Silverlight Web 組件**範本。

4. 在 [**名稱**方塊中，輸入**SLWebPartTest** ，然後選擇**確定**] 按鈕。

    **SharePoint 自訂精靈** 對話方塊隨即出現。

5. 在 **指定偵錯的網站和安全性層級**頁面上，輸入您要偵錯網站定義中，SharePoint 伺服器網站的 URL，或使用預設位置 (http://<em>系統名稱</em>/).

6. 在 **此 SharePoint 方案的信任層級為何？** 區段中，選擇**部署為伺服陣列方案**選項按鈕。

    雖然此範例會使用伺服器陣列方案，Silverlight web 組件專案可以部署為伺服陣列或沙箱化方案。 如需有關沙箱化方案與伺服器陣列方案的詳細資訊，請參閱 <<c0> [ 沙箱化方案考量](../sharepoint/sandboxed-solution-considerations.md)。

7. 在 **您要如何關聯 Silverlight Web 組件**一節**指定 Silverlight 組態資訊**頁面上，選擇**建立新的 Silverlight 專案和關聯 web 組件**選項按鈕。

8. 變更**名稱**要**SLApplication**，將**語言**至**Visual Basic**或**Visual C#**，然後將**Silverlight 版本**要**Silverlight 4.0**。

9. 選擇**完成** 按鈕。 專案會出現在**方案總管 中**。

     方案包含兩個專案： 將 Silverlight 應用程式與 Silverlight web 組件。 Silverlight 應用程式會擷取並顯示從 SharePoint 清單資料，以及 Silverlight web 組件裝載 Silverlight 應用程式，讓您在 SharePoint 中檢視它。

## <a name="customize-the-silverlight-application"></a>自訂 Silverlight 應用程式
 新增 Silverlight 應用程式程式碼和設計的項目。

#### <a name="to-customize-the-silverlight-application"></a>若要自訂 Silverlight 應用程式

1.  在 Silverlight 應用程式中加入 System.Windows.Data 的組件參考。 如需詳細資訊，請參閱[如何：新增或移除參考使用加入參考對話方塊](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。

2.  在 **方案總管 中**，開啟捷徑功能表**參考**，然後選擇 **加入服務參考**。

    > [!NOTE]
    >  如果您使用 Visual Basic，您必須選擇**顯示所有檔案**頂端的圖示**方案總管**以顯示**參考**節點。

3.  在位址方塊中的**加入服務參考**對話方塊方塊中，輸入您的 SharePoint 網站的 URL，例如**http://MySPSite**，然後選擇**移** 按鈕。

     當 Silverlight 會尋找 SharePoint OData 服務 ListData.svc 時，它會將位址取代與完整的服務 URL 中。 此範例中，如 http://myserver 會變成 http://myserver/_vti_bin/ListData.svc 。

4.  選擇**確定**按鈕以新增服務參考加入專案中，並使用預設服務名稱 ServiceReference1。

5.  在功能表列上選擇 [建置] > [建置解決方案]。

6.  以 SharePoint 服務為基礎的專案中加入新的資料來源。 若要這樣做，請在功能表列上，選擇**檢視** > **其他 Windows** > **Zdroje dat**。

     **Zdroje dat**視窗會顯示所有可以使用 SharePoint 清單資料，例如工作、 宣告及行事曆。

7.  新增 Silverlight 應用程式的公告清單資料。 您可以將 「 宣告 」，從**Zdroje dat**視窗拖曳至 Silverlight designer。

     這會建立繫結至 SharePoint 網站的公告清單中的方格控制項。

8.  調整大小以適合 Silverlight 頁面的方格控制項。

9. 在 MainPage.xaml 的程式碼檔案 (*MainPage.xaml.cs* Visual C# 或*MainPage.xaml.vb* Visual basic)，加入下列命名空間參考。

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

10. 在類別頂端新增下列變數宣告。

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
     請務必取代*ServerName*預留位置取代為您執行 SharePoint 的伺服器名稱。

12. 新增下列的錯誤處理程序。

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

## <a name="modify-the-silverlight-web-part"></a>修改 Silverlight web 組件
 變更啟用 Silverlight 偵錯 Silverlight web 組件專案中的屬性。

#### <a name="to-modify-the-silverlight-web-part"></a>若要修改 Silverlight web 組件

1.  開啟 Silverlight web 組件專案的捷徑功能表 (**SLWebPartTest**)，然後選擇**屬性**。

2.  在 **屬性** 視窗中，選擇**SharePoint**  索引標籤。

3.  如果尚未選取，請選取**啟用 Silverlight 偵錯 （而不指令碼偵錯）** 核取方塊。

4.  儲存專案。

## <a name="test-the-silverlight-web-part"></a>測試 Silverlight web 組件
 測試新的 Silverlight web 組件在 SharePoint 中以確保其正確地顯示 SharePoint 清單資料。

#### <a name="to-test-the-silverlight-web-part"></a>若要測試 Silverlight web 組件

1.  選擇**F5**鍵來建置和執行 SharePoint 方案。

2.  在 SharePoint 中，在**站台動作**功能表上，選擇**新頁面**。

3.  中**新的頁面** 對話方塊中，輸入標題，例如**SL Web 組件測試**，然後選擇**建立** 按鈕。

4.  在網頁設計工具上**編輯工具**索引標籤上，選擇**插入**。

5.  在索引標籤功能表列上選擇  **Web 組件**。

6.  在 **分類**方塊中，選擇**自訂**資料夾。

7.  在  **Web 組件**清單中，選擇 Silverlight web 組件，然後選擇**新增**按鈕，將 web 組件加入至設計工具。

8.  您已新增的所有對您想要的網頁之後，請選擇**頁面** 索引標籤，然後選擇**儲存並關閉** 工具列上的按鈕。

     Silverlight web 組件應該現在會顯示從 SharePoint 網站的公告資料。 根據預設，頁面會儲存在 SharePoint 網站頁面清單中。

    > [!NOTE]
    >  當存取 Silverlight 中跨網域的資料時，Silverlight 會保護可用來惡意探索 web 應用程式的安全性弱點。 如果您在存取 Silverlight 中的遠端資料時遇到問題，請參閱[讓服務提供跨網域界限](http://go.microsoft.com/fwlink/?LinkId=223276)。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [部署、 發行和升級 SharePoint 方案套件](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
