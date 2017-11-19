---
title: "沙箱化方案考量 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.SandboxedSolutions
- VS.SharePointTools.Security.SandboxedSolutions
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4598b100572bb47fd537e8edad927d78b4f1550
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sandboxed-solution-considerations"></a>Sandboxed Solution Considerations
  *沙箱化方案*是 Microsoft SharePoint 2010，可讓網站集合的使用者上傳自己的自訂程式碼的方案中的功能。 常見的沙箱化方案已上傳自己的 Web 組件的使用者。  
  
 沙箱的 SharePoint 應用程式會執行安全、 受監控的處理序具有存取有限的組件的 Web 伺服陣列中。 Microsoft SharePoint 2010 會使用功能，方案組件庫、 監視、 解決方案和驗證架構的組合，讓沙箱化方案。  
  
## <a name="specifying-project-trust-level"></a>指定專案的信任層級  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]支援透過布林專案屬性的沙箱化方案稱為*沙箱化方案*。 這個屬性可以設定在任何時間，在專案中，或可以指定當您建立的專案中**SharePoint 自訂精靈**。  
  
> [!NOTE]  
>  變更*沙箱化方案*專案建立後的屬性可能會造成驗證錯誤。  
  
 如果方案被視為陣列範圍方案*沙箱化方案*屬性設定為**false**或您選擇**部署為伺服陣列方案**選項。 不過，解決方案不同的方式處理從伺服器陣列方案如果*沙箱化方案*屬性設定為**true**或您選擇**部署為沙箱化方案**在精靈中的選項。  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint 站台階層  
 若要了解如何沙箱化方案的工作，這有助於了 SharePoint 網站是階層式範圍中。 頂端的項目稱為 Web 伺服陣列和其從屬的其他項目：  
  
 Web 伺服陣列  
  
 Web 應用程式 A  
  
 站台集合 A1  
  
 站台 A1a  
  
 Web 應用程式 B  
  
 站台集合 B1  
  
 站台 B1a  
  
 站台 B1b  
  
 站台集合 B2  
  
 站台 B2a  
  
 如您所見，Web 伺服陣列可以包含一或多個 Web 應用程式，又可以包含一或多個網站集合，其中可以有子網站，依此類推。 建立一個網站集合會影響只有該網站集合，且沒有其他變更。 不過，在 Web 伺服陣列層級所做的變更會影響在伺服器陣列上的所有網站集合。  
  
 Windows SharePoint Services (WSS) 3.0 可讓您將解決方案部署到伺服陣列層級中，但[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]可讓您將部署到伺服陣列層級 （伺服器陣列方案） 或網站集合層級 （沙箱化方案）。  
  
## <a name="why-sandboxed-solutions"></a>為什麼沙箱化方案嗎？  
 WSS 3.0，解決方案可能只能部署到伺服陣列層級。 這意味著以適當的潛在危險或造成不穩定的解決方案無法部署影響整個 Web 伺服陣列和所有的其他網站集合和其下執行的應用程式。 不過，藉由使用沙箱化方案，您可以部署方案到伺服陣列、 特定網站集合的子區域。 若要提供額外的保護，方案的組件不載入主要[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]程序 (w3wp.exe)。 相反地，它會載入至不同的處理序 (SPUCWorkerProcess.exe)。 此程序會受到監視，並實施配額和節流，以防止執行有害的活動，例如執行緊密迴圈消耗 CPU 循環的沙箱化方案中的伺服器陣列。  
  
## <a name="site-collection-solution-gallery"></a>方案庫網站集合  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 有一項稱為「方案庫網站集合」的功能。 您可以存取這項功能，從 SharePoint 2010 管理中心] 頁面，或是藉由開啟**網站動作**功能表上，選擇**站台設定**，然後選擇 [**解決方案**連結底下**圖庫**SharePoint 網站中。 方案組件庫是儲存機制的解決方案，可讓網站集合管理員來管理其網站集合中的方案。  
  
 解決方案資源庫是儲存在根網站的 SharePoint 網站文件庫。 解決方案資源庫取代網站範本，並支援方案套件。 上傳 SharePoint 方案套件 (.wsp) 檔案時，它會處理做為沙箱化方案。  
  
## <a name="sandboxed-solution-limitations"></a>沙箱化方案限制  
 沙箱化方案部署時，陣列的 SharePoint 功能可供其使用僅限於有助於減少可能存在安全性弱點的。 這些限制包括下列：  
  
-   沙箱化方案必須限制可部署的方案項目提供給他們的子集。 可能有弱點的 SharePoint 專案範本，如網站定義和工作流程，沒有可用。  
  
-   SharePoint 會執行沙箱化方案程式碼的處理序 (SPUCWorkerProcess.exe) 中獨立於主[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]應用程式集區 (w3wp.exe) 處理序。  
  
-   對應的資料夾不能加入至專案。  
  
-   中的型別[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Microsoft.Office.Server 不能用在沙箱化方案的組件。 此外，只會在輸入[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]Microsoft.SharePoint 可用沙箱化方案中的組件。  
  
 請務必注意因為沙箱化方案具有 SharePoint 伺服器上不會影響該指定 SharePoint 方案它只會判斷 SharePoint 專案部署至從 SharePoint 的方式[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]哪些組件它將繫結至。 不會影響產生的.wsp 檔案，且.wsp 檔案的直接相互關聯到任何資料*沙箱化方案*屬性。  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>功能與沙箱化方案中的項目  
 沙箱化方案支援下列功能和項目：  
  
-   內容的類型欄位  
  
-   自訂動作  
  
-   宣告式工作流程  
  
-   事件接收器  
  
-   功能圖說文字  
  
-   清單定義  
  
-   清單執行個體  
  
-   模組/檔案  
  
-   巡覽  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   衍生自的所有網頁組件的支援`System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web 組件  
  
-   WebTemplate 功能元素 （而不是 Webtemp.xml)  
  
-   視覺 Web 組件  
  
 沙箱化方案不支援下列功能和項目：  
  
-   應用程式頁面  
  
-   自訂動作群組  
  
-   陣列範圍的功能  
  
-   `HideCustomAction` 項目  
  
-   Web 應用程式範圍的功能  
  
-   程式碼的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [差異沙箱化方案與伺服器陣列方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  