---
title: 逐步解說： 匯入自訂主版頁面和網站的映像上 |Microsoft Docs
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
ms.openlocfilehash: ea327f48bb1a1b04aa4b20601b8bdb3f7dfbb847
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634676"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>逐步解說： 匯入自訂主版頁面和網站頁面的映像
  本逐步解說示範如何匯入 SharePoint 自訂主版頁面及擁有影像的網站頁面[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint 專案。  
  
 本逐步解說示範如何完成下列工作：  
  
-   在 SharePoint Designer 中使用映像，即可建立自訂主版頁面和網站頁面。  
  
-   匯出至 SharePoint 方案的自訂主版頁面、 影像和站台 頁面 (*.wsp*) 檔案。  
  
-   匯入和部署 *.wsp*檔案載入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]使用匯入 SharePoint 方案套件專案的 SharePoint 專案。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您必須擁有下列元件，才能完成此逐步解說：  
  
-   支援的版本[!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)]和 SharePoint。  
  
-   Visual Studio。  
  
-   SharePoint Designer 2010。  
  
## <a name="create-items-in-sharepoint-designer"></a>在 SharePoint Designer 中建立項目
 此範例示範如何在 SharePoint Designer 中建立三個項目，匯出： 自訂主版頁面，參考自訂主版頁面中和要出現在 [網站] 頁面上的影像檔的網站頁面。 影像會新增至 SharePoint 的 /images/ 資料夾中。  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>若要在 SharePoint Designer 建立自訂主版頁面
  
1.  在 SharePoint Designer 中瀏覽窗格中，選擇**主版頁面**站台物件。  
  
2.  在 **主版頁面**功能區中，選擇**空白的主版頁面**。  
  
3.  選擇新的主版頁面，然後在**主版頁面**功能區中，選擇**編輯檔案**。  
  
4.  在 SharePoint Designer 的底部，選擇**程式碼** 索引標籤。  
  
5.  以下列標記取代現有的標記。  
  
    ```aspx-csharp  
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
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>將影像加入 SharePoint Designer 中的內容資料庫
 現在您可以新增要在站台 頁面上顯示的影像。 映像部署到 SharePoint 內容資料庫。  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>若要將影像加入 SharePoint Designer 中的內容資料庫
  
1.  在 [導覽] 窗格中，選擇**所有的檔案**站台物件，然後在樹狀結構檢視中，選擇**映像**資料夾。  
  
2.  在上**的所有檔案**功能區中，選擇**匯入檔案**，選擇您選擇的檔案，然後選擇**確定** 按鈕。 在此範例中，檔案名稱為**myimg1.png**。  
  
     （選擇性） 您可以建立子資料夾，以幫助您組織的映像。  
  
3.  關閉**匯入** 對話方塊。  
  
## <a name="create-a-site-page"></a>建立站台 頁面
 此基本網站頁面使用自訂主版頁面，並顯示您在上一個步驟中加入的映像。  
  
#### <a name="to-create-a-site-page"></a>若要建立的網站頁面  
  
1.  在 [導覽] 窗格中，選擇**網頁**物件。  
  
2.  上**頁**功能區中，選擇**頁面**按鈕，並選擇**ASPX**  頁面中輸入，並接著新的檔案**mycontentpage1.aspx**。  
  
     （選擇性） 您可以建立子資料夾，以幫助您組織的網站頁面。  
  
3.  在 [站台頁] 清單中，選擇**MyContentPage1.aspx**以開啟其屬性頁面，然後在頁面底部，選擇**編輯檔案**連結。  
  
     如果出現訊息並顯示此頁面不包含任何區域。 在安全模式中編輯並詢問您是否想要在進階模式中開啟此頁面，請選擇**是** 按鈕。  
  
4.  在頁面底部，選擇**程式碼** 按鈕。  
  
5.  以下列標記取代現有的標記。  
  
    ```aspx-csharp  
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
  
6.  儲存更新的網站頁面。  
  
## <a name="export-the-items-from-sharepoint"></a>從 SharePoint 匯出的項目
 從 SharePoint 將項目匯出至 SharePoint 方案 (*.wsp*) 檔案。  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>若要從 SharePoint Designer 匯出項目
  
1.  在 SharePoint Designer 中瀏覽窗格中，選擇**小組網站**物件，然後在**站台**功能區中，選擇 **儲存成範本**。  
  
2.  在 **另存為範本**對話方塊方塊中，輸入檔案名稱和範本名稱，然後選取**內容包含**核取方塊，，然後選擇  **確定**  按鈕。  
  
     這會將儲存的內容中的站台 *.wsp*檔案。  
  
3.  解決方案會將匯出之後，請選擇**解決方案資源庫**連結可顯示可用的方案檔的清單。  
  
4.  開啟新的快顯功能表 *.wsp*檔案，然後再選擇**另存目標**將它儲存至系統。  
  
## <a name="import-the-items-into-visual-studio"></a>匯入到 Visual Studio 中的項目
 匯入 *.wsp*檔案載入[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 在匯入內容之後，您可以進行自訂、 新增更多的項目，然後將它部署。  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>將項目從.wsp 檔案匯入 Visual Studio  
  
1.  在  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]，建立**匯入 SharePoint 2010 方案套件**專案。  
  
2.  在上**選取要匯入項目**頁面的 [**模組**中**型別**] 欄中，選取核取方塊只會將檔案匯入表中。  
  
    |檔案名稱|描述|  
    |---------------|-----------------|  
    |\_catalogsmasterpage\_|自訂主版頁面。|  
    |images_|在 SharePoint 檔案系統映像檔。|  
    |SitePages_|[網站] 頁面中。|  
  
3.  選擇**完成**匯入選取的項目 按鈕。  
  
4.  中**方案總管**，選擇\_catalogsmasterpage\_節點，並將值其**部署衝突解決**屬性設**自動**.  
  
     這有助於確保任何部署衝突會自動解決。  
  
5.  如果您新的主版頁面有同名的現有頁面，請確定現有的頁面不會標示為預設主版頁面或在 SharePoint Designer 自訂主版頁面。  
  
     如果現有的主版頁面會標示為預設主版頁面或自訂主版頁面中，您會部署錯誤，指出無法刪除的主版頁面。 若要避免這個問題，這樣做：  
  
    -   如果現有的主版頁面設定為預設主版頁面，暫時設定另一個主版頁面，為預設主版頁面。 您將檔案部署到 SharePoint 之後，請為預設主版頁面中設定新的主版頁面。  
  
    -   如果現有的主版頁面設定為自訂主版頁面，暫時設定另一個主版頁面，為自訂主版頁面。 您將檔案部署至 SharePoint 之後，請為自訂主版頁面中設定新的主版頁面。  
  
6.  在功能表列上選擇 **建置** > **部署方案**。  
  
7.  開啟 SharePoint 網站檢視已部署的項目。  
  
 檔案匯入的替代方法[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]並將其部署到 SharePoint 會將檔案新增至模組中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [如何： 匯入的主版頁面或佈景主題](../sharepoint/how-to-import-a-master-page-or-theme.md)並[使用模組來包含方案中的檔案](../sharepoint/using-modules-to-include-files-in-the-solution.md)。  
  
## <a name="see-also"></a>另請參閱
 [從現有的 SharePoint 網站匯入項目](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)   
 [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
