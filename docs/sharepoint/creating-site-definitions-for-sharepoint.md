---
title: 建立適用於 SharePoint 的站台定義 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 66e3566b7bfabb7ec2049632937beaa697246403
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868322"
---
# <a name="create-site-definitions-for-sharepoint"></a>建立適用於 SharePoint 的網站定義
  中的 SharePoint 網站定義專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]可讓您建立*站台定義*，做為新的 SharePoint 網站的基礎。 這些定義不只會決定的外觀和行為的 SharePoint 網站，但也其預設內容和功能。 在定義中，您可以輸入預先設定的清單、 內容類型、 事件接收器、 影像和其他項目。 例如，SharePoint 包含了一些網站定義 (例如 BLOG)。 當您建立站台上的部落格網站定義時，此網站包含清單、 Web 組件和部落格網站需要的其他項目。  
  
 如需網站定義的詳細資訊，請參閱[網站範本和定義](http://go.microsoft.com/fwlink/?LinkId=179134)。  
  
## <a name="site-definition-projects"></a>網站定義專案
 網站定義專案[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]提供只需要在 SharePoint 網站的基本檔案，但不提供任何預設功能。 您必須將檔案和內容，以提供您想要的功能。 您可以建立並加入您所需要的檔案，以手動的方式，建置網站。  
  
## <a name="feature-stapling"></a>功能裝訂
 建立網站定義中的一個好處[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]是，它們會自動使用*功能裝訂*。 功能裝訂至站台定義而不是將其功能內嵌在網站定義本身中附加功能。 如此一來，可讓您將功能新增至所使用的網站定義，而不需要修改原始的網站定義建立的任何網站。 如需詳細資訊，請參閱 <<c0> [ 功能裝訂](http://go.microsoft.com/fwlink/?LinkID=119283)。  
  
## <a name="site-definition-project-components"></a>網站定義專案元件
 當您建立網站定義方案時，將下列的預設檔案新增至其**SiteDefinition**節點。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|*Default.aspx*|新的 SharePoint 網站預設 ASPX 首頁。|  
|*Onet.xml*|指定新的站台組態]、 [站台定義範本，以及預設行為的元件。 這些設定可以包含屬性的內容類型都已啟用，預設清單檢視中，文件範本檔案，例如，與 Web 組件包含與站台。 根據預設，`Modules`區段會列出可以加入至 SharePoint 網站和設定方式的檔案。|  
|*webtemp_\<SiteDefinitionName >.xml*|指定出現在站台定義組態**範本選擇**一節**新的 SharePoint 網站**頁面。|  
  
 根據預設，所有的站台定義會儲存在*\<磁碟機： > \Program Files\Common Files\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates*資料夾。 每個網站定義都有它自己的子資料夾。  
  
## <a name="related-topics"></a>相關主題
  
|標題|描述|  
|-----------|-----------------|  
|[逐步解說：建立基本網站定義專案](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|將引導您逐步建立基本網站定義專案中[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。|  
|[如何：建立自訂網站定義和組態](http://go.microsoft.com/fwlink/?LinkId=183309)|描述如何透過複製現有的站台定義及修改複本，在 SharePoint 中建立的自訂網站定義。|  
|[*WebTemp.xml*](http://go.microsoft.com/fwlink/?LinkId=183310)|描述指定站台可用的定義中的原始檔**範本選擇**一節**新的 SharePoint 網站**頁面。|  
|[當地語系化 SharePoint 方案](../sharepoint/localizing-sharepoint-solutions.md)|描述如何準備您的 SharePoint 解決方案供全域使用。|  
|[建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)|描述如何建立的使用者可以修改 SharePoint 網頁組件。|  
|[建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|描述如何建立可重複使用執行中應用程式頁面和 Web 組件的控制項。|  
|[Visual Web Developer](http://go.microsoft.com/fwlink/?LinkId=178725)|描述如何使用您的專案中開啟網頁時出現的設計工具。|  
|[ASP.NET Web 網頁概觀](http://go.microsoft.com/fwlink/?LinkId=178726)|提供的結構的一般資訊[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]網頁，網頁式的處理方式[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]，以及如何[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面會顯示符合 XHTML 標準的標記。|  
|[ASP.NET Web 網頁語法概觀](http://go.microsoft.com/fwlink/?LinkId=178727)|描述構成 ASP.NET 網頁的標記項目。|  
|[程式設計的 ASP.NET Web Pages](http://go.microsoft.com/fwlink/?LinkId=178728)|提供有關如何建立事件處理常式中的資訊[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]頁面，以及如何使用用戶端指令碼。|  
|[在 Windows SharePoint Services 中進行程式設計](http://go.microsoft.com/fwlink/?LinkId=178729)|描述如何使用受管理的物件模型中所提供[!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]。|  
  
## <a name="see-also"></a>另請參閱
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
