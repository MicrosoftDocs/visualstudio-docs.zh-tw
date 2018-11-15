---
title: 沙箱化方案考量 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2f9a5d0c439d619864cc6e9559608e3c3891fc7e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890032"
---
# <a name="sandboxed-solution-considerations"></a>沙箱化方案考量
  *沙箱化方案*是可讓網站集合的使用者上傳他們自己的自訂程式碼解決方案的 Microsoft SharePoint 2010 中的功能。 常見的沙箱化方案是上傳他們自己的 Web 組件的使用者。  
  
 沙箱化 SharePoint 應用程式會在安全且受監視的程序可存取受限制的 Web 伺服陣列一部分執行。 Microsoft SharePoint 2010 使用功能、 解決方案資源庫、 監視、 解決方案和驗證架構的組合，以啟用沙箱化方案。  
  
## <a name="specify-project-trust-level"></a>指定專案的信任層級
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 支援透過布林值的專案屬性的沙箱化方案稱為*沙箱化方案*。 可以在專案中，隨時設定這個屬性，或者可以指定當您建立的專案中**SharePoint 自訂精靈**。  
  
> [!NOTE]  
>  變更*沙箱化方案*專案建立後的屬性可能會造成驗證錯誤。  
  
 方案會視為陣列範圍的解決方案，如果*沙箱化方案*屬性設定為**false** ，或您選擇**部署為伺服陣列方案**選項。 不過，解決方案是以不同方式處理從伺服器陣列方案如果*沙箱化方案*屬性設定為 **，則為 true** ，或您選擇**部署為沙箱化方案**在精靈中的選項。  
  
## <a name="sharepoint-site-hierarchy"></a>SharePoint 站台階層
 若要了解如何在沙箱化方案的工作，建議您了解 SharePoint 網站是階層式範圍中。 最上層的項目稱為 Web 伺服陣列，而其從屬的其他項目：  
  
 Web 伺服陣列  
  
 Web 應用程式 A  
  
 站台集合 A1  
  
 站台 A1a  
  
 Web 應用程式 B  
  
 站台集合 B1  
  
 站台 B1a  
  
 站台 B1b  
  
 站台集合 B2  
  
 站台 b2a 拓  
  
 如您所見，Web 伺服陣列可以包含一或多個 Web 應用程式，其中可以包含一或多個網站集合，其中可以有子網站，依此類推。 對一個網站集合產生何種影響只有網站集合進行且沒有其他變更。 不過，在 Web 伺服陣列層級所做的變更會影響在伺服器陣列上的所有網站集合。  
  
 Windows SharePoint Services (WSS) 3.0 可讓您將解決方案部署到伺服陣列層級中，但[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]可讓您將部署到伺服陣列層級 （伺服器陣列方案） 或網站集合層級 （沙箱化方案）。  
  
## <a name="why-sandboxed-solutions"></a>為什麼沙箱化方案嗎？
 在 WSS 3.0 中，解決方案可能只能部署到伺服陣列層級。 這表示，具有潛在危害性或不穩定的解決方案無法部署可影響整個 Web 伺服陣列和所有其他網站集合和其下執行的應用程式。 不過，藉由使用沙箱化方案，您可以至伺服器陣列中，在特定網站集合的子區域部署您的解決方案。 若要提供額外的保護，方案的組件不會載入到主要[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]程序 (*w3wp.exe*)。 相反地，它會載入不同的處理序 (*SPUCWorkerProcess.exe*)。 此程序會受到監視，並實作配額和節流，以防止執行有害的活動，例如執行會耗用 CPU 循環的緊密迴圈的沙箱化方案中的伺服器陣列。  
  
## <a name="site-collection-solution-gallery"></a>方案庫網站集合
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 有一項稱為「方案庫網站集合」的功能。 您可以存取這項功能，從 SharePoint 2010 管理中心 頁面，或是藉由開啟**網站動作**功能表上，選擇**站台設定**，然後選擇**解決方案**連結底下**組件庫**SharePoint 網站中。 解決方案資源庫是存放庫的解決方案，可讓網站集合管理員管理其網站集合中的解決方案。  
  
 解決方案資源庫是儲存在根網站的 SharePoint 網站文件庫。 解決方案資源庫會取代網站範本，並支援解決方案套件。 當 SharePoint 方案套件 (*.wsp*) 上傳檔案時，它都處理為沙箱化方案。  
  
## <a name="sandboxed-solution-limitations"></a>沙箱化方案限制
 沙箱化方案部署時，陣列的 SharePoint 功能可供其使用僅限於以減少可能會有任何安全性弱點。 這些限制包括下列：  
  
- 沙箱化方案已部署的方案項目提供給他們的限定的子集。 無法使用可能有弱點的 SharePoint 專案範本，例如網站定義和工作流程。  
  
- SharePoint 會執行處理序中的沙箱化方案程式碼 (*SPUCWorkerProcess.exe*) 不同於主要[!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)]應用程式集區 (*w3wp.exe*) 處理程序。  
  
- 對應的資料夾無法加入至專案。  
  
- 中的型別[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]Microsoft.Office.Server 不能用在沙箱化方案的組件。 此外，只有在型別[!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]Microsoft.SharePoint 可用沙箱化方案中的組件。  
  
  請務必請注意，指定 SharePoint 方案為沙箱化方案就不會影響 SharePoint 伺服器;它只會決定如何將 SharePoint 專案部署至從 SharePoint[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]和組件繫結至。 它不會影響所產生 *.wsp*檔案，而 *.wsp*檔案沒有任何直接相互關聯的資料*沙箱化方案*屬性。  
  
## <a name="capabilities-and-elements-in-sandboxed-solutions"></a>功能與沙箱化方案中的項目
 沙箱化方案支援下列功能和項目：  
  
- 內容的類型欄位  
  
- 自訂動作  
  
- 宣告式工作流程  
  
- 事件接收器  
  
- 功能的圖說文字  
  
- 清單定義  
  
- 清單執行個體  
  
- 模組/檔案  
  
- 巡覽  
  
- *Onet.xml*  
  
- SPItemEventReceiver  
  
- SPListEventReceiver  
  
- SPWebEventReceiver  
  
- 從衍生的所有網頁組件的支援 `System.Web.UI.WebControls.WebParts.WebPart`  
  
- Web 組件  
  
- WebTemplate 功能元素 (而非*Webtemp.xml*)  
  
- 視覺 Web 組件  
  
  沙箱化方案不支援下列功能和項目：  
  
- 應用程式頁面  
  
- 自訂動作群組  
  
- 陣列範圍的功能  
  
- `HideCustomAction` 項目  
  
- Web 應用程式範圍的功能  
  
- 使用程式碼的工作流程  
  
## <a name="see-also"></a>另請參閱
 [差異沙箱化方案與伺服器陣列解決方案](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  