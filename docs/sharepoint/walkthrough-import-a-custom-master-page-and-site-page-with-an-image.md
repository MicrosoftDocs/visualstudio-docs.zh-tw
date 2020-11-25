---
title: 使用影像匯入自訂主版頁面 & 網站頁面
description: 在這個逐步解說中，將包含影像的 SharePoint 自訂主版頁面和網站頁面匯入 Visual Studio 的 SharePoint 專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ceb69608a2d1770f082991f3d927d4e4639ae56
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970151"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>逐步解說：使用影像匯入自訂主版頁面和網站頁面
  本逐步解說將示範如何將 SharePoint 自訂主版頁面及包含影像的網站頁面匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 專案。

 本逐步解說將說明如何完成下列工作：

- 使用 SharePoint Designer 中的影像建立自訂主版頁面和網站頁面。

- 將自訂主版頁面、影像和網站頁面匯出至 SharePoint 方案， (*.wsp*) 檔。

- 使用 [匯入 SharePoint 方案套件] 專案，將 *.wsp* 檔案匯入並部署到 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 專案。

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 您必須具有下列元件，才能完成此逐步解說：

- 支援的 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 和 SharePoint 版本。

- Visual Studio。

- SharePoint Designer 2010。

## <a name="create-items-in-sharepoint-designer"></a>在 SharePoint Designer 中建立專案
 此範例示範如何在 SharePoint Designer 中建立三個用於匯出的專案：自訂主版頁面、參考自訂主版頁面的網站頁面，以及要顯示在網站頁面上的影像檔案。 影像會新增至 SharePoint 中的/images/資料夾。

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>在 SharePoint Designer 中建立自訂主版頁面

1. 在 SharePoint Designer 的流覽窗格中，選擇 **主版頁面** 的網站物件。

2. 在 [ **主版頁面** ] 功能區中，選擇 [ **空白主版頁面**]。

3. 選擇新的主版頁面，然後在 **主版頁面** 功能區上，選擇 [ **編輯** 檔案]。

4. 在 SharePoint Designer 底部，選擇 [程式 **代碼** ] 索引標籤。

5. 將現有標記取代為下列標記。

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

6. 儲存頁面，選擇 [**主版頁面**] 索引標籤，然後將主版頁面重新命名為 **mybasic1。**

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>將影像加入至 SharePoint Designer 中的內容資料庫
 現在您可以新增要在網站頁面上顯示的影像。 映射會部署到 SharePoint 內容資料庫。

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>將影像加入至 SharePoint Designer 中的內容資料庫

1. 在流覽窗格中，選擇 [ **所有** 檔案] 網站物件，然後在樹狀檢視中選擇 [ **images** ] 資料夾。

2. 在 [ **所有** 檔案] 功能區上，選擇 [匯 **入** 檔案]，選擇您選擇的檔案，然後選擇 [ **確定]** 按鈕。 在此範例中，檔案的名稱為 **myimg1.png**。

     您可以選擇性地建立子資料夾，以協助組織影像。

3. 關閉 [匯 **入** ] 對話方塊。

## <a name="create-a-site-page"></a>建立網站頁面
 這個基本網站頁面使用自訂主版頁面，並顯示您在前一個步驟中新增的影像。

#### <a name="to-create-a-site-page"></a>若要建立網站頁面

1. 在流覽窗格中，選擇 [ **網站頁面** ] 物件。

2. 在 [ **頁面** ] 功能區上，選擇 [ **頁面** ] 按鈕，選擇 [ **ASPX** ] 頁面類型，然後將新的檔案命名為 **mycontentpage1 .aspx**。

     您可以選擇性地建立子資料夾，以協助組織網站頁面。

3. 在 [網站頁面] 清單中，選擇 [ **MyContentPage1** ] 開啟其 [屬性] 頁面，然後在頁面底部選擇 [ **編輯** 檔案] 連結。

     如果出現一則訊息，指出此頁面未包含任何可在安全模式中編輯的區域，並詢問您是否要在 [advanced] 模式中開啟此頁面，請選擇 [ **是]** 按鈕。

4. 在頁面底部，選擇 [程式 **代碼** ] 按鈕。

5. 將現有標記取代為下列標記。

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

6. 儲存更新的網站頁面。

## <a name="export-the-items-from-sharepoint"></a>從 SharePoint 匯出專案
 從 SharePoint 將專案匯出至 SharePoint 方案， (*.wsp*) 檔。

#### <a name="to-export-items-from-sharepoint-designer"></a>從 SharePoint Designer 匯出專案

1. 在 SharePoint Designer 的流覽窗格中，選擇 [ **小組網站** ] 物件，然後在 [ **網站** ] 功能區中選擇 [ **另存** 新檔範本]。

2. 在 [ **另存** 新檔範本] 對話方塊中，輸入檔案名和範本名稱，選取 [ **包含內容** ] 核取方塊，然後選擇 [ **確定]** 按鈕。

     這會將網站的內容儲存在 *.wsp* 檔案中。

3. 匯出解決方案之後，請選擇 [ **方案庫** ] 連結，以顯示可用的方案檔清單。

4. 開啟新 *.wsp* 檔案的快捷方式功能表，然後選擇 [ **另存目標** ]，將它儲存至系統。

## <a name="import-the-items-into-visual-studio"></a>將專案匯入 Visual Studio
 將 *.wsp* 檔案匯入至 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 匯入內容之後，您可以自訂內容、新增更多專案，然後加以部署。

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>將專案從 .wsp 檔匯入 Visual Studio

1. 在中 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ，建立 [匯 **入 SharePoint 2010 方案套件** ] 專案。

2. 在 [**選取要匯入的專案**] 頁面上，于 [**類型**] 資料行中的 [**模組**] 下，選取要匯入之下表中檔案的核取方塊。

   | 檔案名稱 | 描述 |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | 自訂主版頁面。 |
   | images_ | SharePoint 檔案系統中的影像檔案。 |
   | SitePages_ | 網站頁面。 |

3. 選擇 [ **完成]** 按鈕以匯入選取的專案。

4. 在 **方案總管** 中，選擇 [ \_ catalogsmasterpage] \_ 節點，並將其 [ **部署衝突解決** 方式] 屬性的值設定為 [ **自動**]。

    這有助於確保自動解決任何部署衝突。

5. 如果新的主版頁面與現有頁面的名稱相同，請確定現有頁面未標示為預設主版頁面或 SharePoint Designer 中的自訂主版頁面。

    如果現有的主版頁面標示為預設主版頁面或自訂主版頁面，您將會收到部署錯誤，指出無法刪除主版頁面。 若要避免這個問題，請執行下列動作：

   - 如果現有的主版頁面設定為預設的主版頁面，請暫時將另一個主版頁面設定為預設主版頁面。 將檔案部署至 SharePoint 之後，請將新的主版頁面設定為預設主版頁面。

   - 如果現有的主版頁面設定為自訂主版頁面，請暫時將另一個主版頁面設定為自訂主版頁面。 將檔案部署至 SharePoint 之後，請將新的主版頁面設定為自訂主版頁面。

6. 在功能表列上，選擇 [**建立**  >  **部署方案**]。

7. 開啟 SharePoint 網站以查看已部署的專案。

   將檔案匯入和部署到 SharePoint 的另一種方式是將檔案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 新增至中的模組 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。 [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][如何：匯入主版頁面或主題](../sharepoint/how-to-import-a-master-page-or-theme.md)，並[使用模組來包含方案中的](../sharepoint/using-modules-to-include-files-in-the-solution.md)檔案。

## <a name="see-also"></a>另請參閱
- [從現有的 SharePoint 網站匯入專案](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
