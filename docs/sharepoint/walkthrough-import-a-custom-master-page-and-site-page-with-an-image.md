---
title: 逐步解說： 匯入自訂主版頁面和網站上的映像 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f90f85e7f22cf3bdecf90aaf6f8d61af3f399a68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>逐步解說：匯入自訂主版頁面及包含影像的網站頁面
  本逐步解說示範如何匯入 SharePoint 自訂主版頁面和網站頁面，其中包含影像變成[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。  
  
 本逐步解說示範如何完成下列工作：  
  
-   在 SharePoint Designer 中使用的映像建立自訂主版頁面和網站頁面。  
  
-   匯出自訂主版頁面、 影像和站台頁面至 SharePoint 方案 (.wsp) 檔案。  
  
-   匯入和部署成.wsp 檔案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入 SharePoint 方案套件專案的 SharePoint 專案。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您必須擁有下列元件才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [開發 SharePoint 方案的需求](../sharepoint/requirements-for-developing-sharepoint-solutions.md)。  
  
-   Visual Studio。  
  
-   SharePoint Designer 2010。  
  
## <a name="create-items-in-sharepoint-designer"></a>在 SharePoint Designer 中建立項目  
 這個範例示範如何在 SharePoint Designer 中建立三個項目，匯出： 自訂主版頁面、 網站頁面以參考自訂主版頁面和要顯示在 [網站] 頁面上的映像檔。 影像會新增至 SharePoint 的 /images/ 資料夾。  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>若要在 SharePoint Designer 中建立自訂主版頁面  
  
1.  在 SharePoint Designer 中的導覽窗格中，選擇**主版頁面**站台物件。  
  
2.  在**主版頁面**功能區中，選擇**空白主版頁面**。  
  
3.  選擇新的主版頁面，然後在**主版頁面**功能區中，選擇**編輯檔案**。  
  
4.  在 SharePoint Designer 的底部，選擇**程式碼** 索引標籤。  
  
5.  以下列標記取代現有的標記。  
  
    ```  
    <%@ Master Language="C#" %>  
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <html dir="ltr">  
    <head runat="server">  
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">  
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>  
    <title>Web Page</title>  
    </head>  
    <body>  
    <form id="form1" runat="server">  
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"   
            runat="server">  
          </asp:ContentPlaceHolder>  
    </form>  
    </body>  
    </html>  
    ```  
  
6.  儲存頁面中，選擇**主版頁面**索引標籤，然後重新命名為主版頁面**mybasic1.master**。  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>在 SharePoint Designer 中的內容資料庫中加入影像  
 現在您可以加入要在站台設定 頁面上顯示影像。 映像部署到 SharePoint 內容資料庫。  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>在 SharePoint Designer 中的內容資料庫中新增映像  
  
1.  在瀏覽窗格中，選擇 **所有檔案**站台物件，然後在樹狀結構檢視中，選擇**映像**資料夾。  
  
2.  在**所有檔案**功能區中，選擇**匯入檔案**，選擇您選擇的檔案，然後選擇**確定** 按鈕。 在此範例中，檔案會命名為**myimg1.png**。  
  
     （選擇性） 您可以建立子資料夾，以協助您組織的映像。  
  
3.  關閉**匯入** 對話方塊。  
  
## <a name="create-a-site-page"></a>建立站台頁面  
 本頁基本站台使用自訂主版頁面，並顯示您在上一個步驟中加入的映像。  
  
#### <a name="to-create-a-site-page"></a>若要建立站台頁面  
  
1.  在瀏覽窗格中，選擇 **網站頁面**物件。  
  
2.  在**頁面**功能區中，選擇**頁面**按鈕，選擇**ASPX**  頁面中輸入，並再將新檔案**mycontentpage1.aspx**。  
  
     （選擇性） 您可以建立子資料夾，以協助您組織的網站頁面。  
  
3.  在 站台頁 清單中，選擇  **MyContentPage1.aspx**來開啟其屬性頁面，然後在頁面底部，選擇**編輯檔**連結。  
  
     如果出現訊息並顯示此頁面未包含任何區域。 在安全模式中編輯並詢問您是否想要在進階模式下開啟此頁面，請選擇**是** 按鈕。  
  
4.  在頁面底部，選擇**程式碼** 按鈕。  
  
5.  以下列標記取代現有的標記。  
  
    ```  
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>  
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>  
    <%@ Import Namespace="Microsoft.SharePoint" %>  
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>  
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>  
  
    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">  
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />  
    </asp:Content>  
    ```  
  
6.  儲存更新的站台。  
  
## <a name="export-the-items-from-sharepoint"></a>從 SharePoint 匯出項目  
 從 SharePoint 的項目匯出至 SharePoint 方案 (.wsp) 檔案中。  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>若要從 SharePoint Designer 匯出項目  
  
1.  在 SharePoint Designer 中的導覽窗格中，選擇**小組網站**物件，然後在**網站**功能區中，選擇**儲存成範本**。  
  
2.  在**另存為範本**對話方塊方塊中，輸入檔案名稱和範本名稱，選取**內容包含**核取方塊，，然後選擇 **確定**按鈕。  
  
     這會將網站的內容儲存.wsp 檔案中。  
  
3.  方案會將匯出之後，請選擇**解決方案資源庫**連結，顯示可用的方案檔的清單。  
  
4.  開啟新的.wsp 檔案的捷徑功能表，然後選擇**另存目標**將它儲存到系統。  
  
## <a name="import-the-items-into-visual-studio"></a>匯入到 Visual Studio 中的項目  
 .wsp 檔案匯入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 在匯入內容之後，進行自訂、 新增更多的項目，並再將它部署。  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>若要匯入 Visual Studio 從.wsp 檔案的項目  
  
1.  在[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立**匯入 SharePoint 2010 方案套件**專案。  
  
2.  在**選取要匯入項目**頁面的 **模組**中**類型**資料行中，選取核取方塊只將檔案匯入下表中。  
  
    |檔案名稱|描述|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|自訂主版頁面。|  
    |images_|SharePoint 檔案系統中影像檔。|  
    |SitePages_|[網站] 頁面中。|  
  
3.  選擇**完成**匯入選取的項目 按鈕。  
  
4.  中**方案總管 中**，選擇 _catalogsmasterpage\_  節點，設定的值和其**部署衝突解決**屬性**自動**。  
  
     這有助於確保任何部署衝突會自動解決。  
  
5.  如果新的主版頁面都有同名的現有頁面，請確定現有的頁面未標示為預設主版頁面或在 SharePoint Designer 中的自訂主版頁面。  
  
     如果現有的主版頁面標示為預設主版頁面或自訂主版頁面時，就會部署錯誤，指出無法刪除的主版頁面。 若要避免這個問題，這樣做：  
  
    -   如果現有的主版頁面設定為預設主版頁面中，暫時將另一個主版頁面設定為預設主版頁面。 將檔案部署至 SharePoint 之後，請以預設主版頁面設定新的主版頁面。  
  
    -   如果現有的主版頁面設定為自訂主版頁面中，暫時將另一個主版頁面設定為自訂主版頁面。 將檔案部署至 SharePoint 之後，請為自訂主版頁面中設定新的主版頁面。  
  
6.  在功能表列上選擇 **建置**，**部署方案**。  
  
7.  開啟 SharePoint 網站檢視已部署的項目。  
  
 檔案匯入的替代方式[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]並將其部署到 SharePoint 會將檔案新增至模組中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [如何： 匯入的主版頁面或佈景主題](../sharepoint/how-to-import-a-master-page-or-theme.md)和[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [從現有的 SharePoint 網站匯入的項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  