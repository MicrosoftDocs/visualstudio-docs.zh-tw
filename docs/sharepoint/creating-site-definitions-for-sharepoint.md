---
title: "建立 SharePoint 的站台定義 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
ms.assetid: 83db570d-6b9f-4dab-9e71-db41f17b987a
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a4a7c002bd17da5f693955a82ab2e74bf65dc0cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="creating-site-definitions-for-sharepoint"></a>建立 SharePoint 的站台定義
  中的 SharePoint 網站定義專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可讓您建立*網站定義*，做為新的 SharePoint 網站的基礎。 這些定義不只會決定的外觀和行為的 SharePoint 網站，但也其預設內容和功能。 在定義中，您可以將預先設定的清單、 內容類型、 事件接收器、 影像和其他項目。 例如，SharePoint 包含了一些網站定義 (例如 BLOG)。 當您建立部落格網站定義為基礎的站台時，此網站包含清單、 Web 組件和部落格網站需要的其他項目。  
  
 如需網站定義的詳細資訊，請參閱[網站範本及定義](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## <a name="site-definition-projects"></a>網站定義專案  
 網站定義中的專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供只需要在 SharePoint 網站的基本檔案，但不提供任何預設功能。 您必須將檔案和內容，以提供您想要的功能。 您可以藉由建立加入您所需要的檔案，手動建立站台。  
  
## <a name="feature-stapling"></a>裝訂功能  
 建立網站定義中的其中一個優點[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]是，它們會自動使用*裝訂功能*。 功能裝訂附加至站台定義，而不是將其功能內嵌在站台定義本身的功能。 如此一來，可讓您將功能加入至任何站台使用站台定義而不修改原始的站台定義建立的。 如需詳細資訊，請參閱[裝訂功能](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## <a name="site-definition-project-components"></a>網站定義專案元件  
 當您建立網站定義方案時，下列的預設檔案會新增至其**SiteDefinition**節點。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|default.aspx|新的 SharePoint 網站預設 ASPX 首頁。|  
|Onet.xml|指定新的站台組態]、 [站台定義範本，以及預設行為的元件。 這些設定可以包含屬性的內容類型已啟用，預設清單檢視中，文件範本檔案，例如，Web 組件包含與站台。 根據預設，`Modules`區段會列出要加入至 SharePoint 網站和設定方式的檔案。|  
|webtemp_*SiteDefinitionName*.xml|指定出現在站台定義設定**範本選擇**區段**新的 SharePoint 網站**頁面。|  
  
 根據預設，所有的站台定義會儲存在*磁碟機：*\Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates 資料夾。 每個站台定義都有它自己的子資料夾。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[逐步解說：建立基本網站定義專案](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|將引導您逐步完成建立基本網站定義專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。|  
|[如何： 建立自訂網站定義和設定](http://go.microsoft.com/fwlink/?LinkId=183309)|描述如何在 SharePoint 中建立自訂網站定義複製現有的站台定義，然後再修改該複本。|  
|[WebTemp.xml](http://go.microsoft.com/fwlink/?LinkId=183310)|描述指定的站台定義中提供的原始檔**範本選擇**區段**新的 SharePoint 網站**頁面。|  
|[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)|描述如何準備您的 SharePoint 方案供全域使用。|  
|[建立 SharePoint 的 Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)|描述如何建立的使用者可以修改 SharePoint 網頁組件。|  
|[為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|描述如何建立可重複使用執行中應用程式頁面和 Web 組件的控制項。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|描述如何使用您在專案中開啟網頁時，會出現在設計工具。|  
|[ASP.NET Web Pages 概觀](http://go.microsoft.com/fwlink/?LinkId=178726)|提供一般資訊的結構[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]Web pages，處理頁面的方式[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]，以及如何[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面會顯示符合 XHTML 標準的標記。|  
|[ASP.NET Web 網頁語法](http://go.microsoft.com/fwlink/?LinkId=178727)|描述組成 ASP.NET 網頁的標記項目。|  
|[程式設計 ASP.NET Web 網頁](http://go.microsoft.com/fwlink/?LinkId=178728)|提供有關如何建立事件處理常式中的資訊[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面，以及如何使用用戶端指令碼。|  
|[在 Windows SharePoint Services 中程式設計](http://go.microsoft.com/fwlink/?LinkId=178729)|描述如何使用受管理的物件模型中所提供[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]。|  
  
## <a name="see-also"></a>另請參閱  
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  