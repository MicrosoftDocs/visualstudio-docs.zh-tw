---
title: 建立 SharePoint 的網站定義 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015062"
---
# <a name="create-site-definitions-for-sharepoint"></a>建立 SharePoint 的網站定義
  中的 SharePoint 網站定義專案可 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 讓您建立*網站定義*，作為新 SharePoint 網站的基礎。 這些定義不只會決定 SharePoint 網站的外觀和行為，還會判斷其預設內容和功能。 在定義中，您可以放入預先設定的清單、內容類型、事件接收器、影像和其他項目。 例如，SharePoint 包含了一些網站定義 (例如 BLOG)。 當您根據 BLOG 網站定義來建立網站時，網站會包含清單、Web 元件，以及日誌網站所需的其他專案。

 如需網站定義的詳細資訊，請參閱[網站範本和定義](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14))。

## <a name="site-definition-projects"></a>網站定義專案
 中的網站定義專案 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 只提供 SharePoint 網站所需的基本檔案，而不提供任何預設功能。 您必須新增檔案和內容，以提供您想要的功能。 您可以手動建立網站，方法是建立並新增您需要的檔案。

## <a name="feature-stapling"></a>功能裝訂
 在中建立網站定義的其中一個優點 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 是，它們會自動使用*功能裝訂*。 功能裝訂會將功能附加至網站定義，而不是在網站定義本身內嵌其功能。 這麼做可讓您將功能新增至使用網站定義所建立的任何網站，而不需要修改原始網站定義。 如需詳細資訊，請參閱[功能裝訂](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12))。

## <a name="site-definition-project-components"></a>網站定義專案元件
 當您建立網站定義解決方案時，會將下列預設檔案新增至其**SiteDefinition**節點。

|檔案名稱|描述|
|---------------|-----------------|
|*default.aspx*|新 SharePoint 網站的預設 ASPX 首頁。|
|*onet.xml*|指定新網站的設定、網站定義範本的元件，以及預設行為。 這些設定可以包含屬性，例如已啟用的內容類型、預設清單視圖、檔範本檔案，以及網站所包含的 Web 元件。 根據預設， `Modules` 區段會列出要加入至 SharePoint 網站的檔案，以及這些檔案的設定方式。|
|*webtemp_ \<SiteDefinitionName> .xml*|指定出現在 [**新增 SharePoint 網站**] 頁面的 [**範本選擇**] 區段中的網站定義設定。|

 根據預設，所有網站定義都會儲存在* \<drive:> \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates*資料夾中。 每個網站定義都有自己的子資料夾。

## <a name="related-topics"></a>相關主題

|Title|描述|
|-----------|-----------------|
|[逐步解說：建立基本網站定義專案](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|引導您逐步完成在中建立基本網站定義專案的步驟 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 。|
|[How to：建立自訂網站定義和設定](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|說明如何複製現有的網站定義，然後修改複本，以在 SharePoint 中建立自訂網站定義。|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|描述在 [**新增 SharePoint 網站**] 頁面的 [**範本選擇**] 區段中，指定可用網站定義的原始檔案。|
|[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)|說明如何準備 SharePoint 解決方案以供全域使用。|
|[建立 SharePoint 的 web 元件](../sharepoint/creating-web-parts-for-sharepoint.md)|描述如何建立可供使用者修改的 SharePoint 網頁元件。|
|[為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|描述如何建立可重複使用的控制項，以在應用程式頁面和 Web 組件中執行。|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|描述如何使用當您在專案中開啟網頁時，所顯示的設計工具。|
|[ASP.NET Web Pages 總覽](/previous-versions/aspnet/428509ah(v=vs.100))|提供有關 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 網頁結構、如何處理頁面 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ，以及 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 頁面如何顯示符合 XHTML 標準之標記的一般資訊。|
|[ASP.NET 網頁語法](/previous-versions/aspnet/k33801s3(v=vs.100))|描述構成 ASP.NET 網頁的標記元素。|
|[程式設計 ASP.NET Web Pages](/previous-versions/aspnet/0yt4zca8(v=vs.100))|提供如何在頁面中建立事件處理常式 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] ，以及如何使用用戶端腳本的相關資訊。|
|[Windows SharePoint Services 中的程式設計](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|描述如何使用中提供的 managed 物件模型 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 。|

## <a name="see-also"></a>另請參閱
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
