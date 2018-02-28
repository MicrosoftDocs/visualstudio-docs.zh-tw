---
title: "專案子類型設計 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 126bee146d1f53233db3c14672f80da4c0d60e9e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes-design"></a>專案子類型設計
專案子類型可讓 Vspackage 延伸 Microsoft Build Engine (MSBuild) 為基礎的專案。 使用彙總可讓您重複使用的核心管理專案系統中實作大量[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]卻仍然來自訂特定案例的行為。  
  
 下列主題將詳細說明的基本設計和實作專案子類型：  
  
-   專案子類型的設計。  
  
-   多層級的彙總。  
  
-   支援的介面。  
  
## <a name="project-subtype-design"></a>專案子類型設計  
 專案子類型的初始化達成彙總主要<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>物件。 此彙總可讓專案子類型，來覆寫或加強大部分的基底的專案功能。 專案子類型會取得第一個有機會處理屬性使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>，命令使用<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>，和專案項目管理使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>。 也可以擴充專案子類型：  
  
-   專案組態的物件。  
  
-   組態相關的物件。  
  
-   瀏覽 組態無關的物件。  
  
-   Automation 物件的專案。  
  
-   專案 automation 屬性集合。  
  
 如需有關專案子類型的擴充性的詳細資訊，請參閱[屬性和方法擴充的專案子類型](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。  
  
##### <a name="policy-files"></a>原則檔  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境提供的擴充基底專案系統專案子類型中實作的原則檔與範例。 原則檔可讓的成形[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由管理功能，包括 [方案總管] 中，環境**加入專案**對話方塊中，**加入新項目**對話方塊和**屬性** 對話方塊。 原則子類型會覆寫，而且透過這些功能，來增強<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>，`IOleCommandTarget`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>實作。  
  
##### <a name="aggregation-mechanism"></a>彙總機制  
 環境的專案子類型的彙總機制支援多個層級的彙總，如此可讓進階實作的進一步 flavoring 式的專案子類型。 此外，支援物件的專案子類型，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>，已設計成允許多重圖層的層級。 為了保持 COM 和 COM 的條件約束彙總規則、 專案子類型和基底的專案需要程式化合作，以啟用內部的子類型或基底的專案適當地參與委派方法呼叫和管理參考計數. 也就是即將要彙總專案已設計成支援彙總。  
  
 下圖顯示多層級專案子類型彙總的圖解表示法。  
  
 ![Visual Studio multilevel projectflavor 圖形](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS_MultilevelProjectFlavor")  
多層級專案子類型  
  
 多層級專案子類型彙總包含三個層級，基底的專案，專案子類型、 依彙總，然後進一步彙總進階的專案子類型。 圖例著重在某些支援介面的一部分提供[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案子類型的架構。  
  
##### <a name="deployment-mechanisms"></a>部署機制  
 基底專案系統的許多功能增強專案子類型，包括部署機制。 藉由實作介面組態專案子類型會影響的部署機制 (例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>)，藉由呼叫 QueryInterface 上擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>。 在此案例中的專案子類型和進階的專案子類型加入不同的設定實作，呼叫基底專案`QueryInterface`進階的專案子類型上`IUnknown`。 如果內部專案子類型包含基底的專案要求的設定實作，進階的專案子類型會委派給內部專案子類型所提供的實作。 做為保存到另一個彙總層級狀態的機制，實作的專案子類型的所有層級<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>保存非組建將 XML 資料相關的專案檔。 如需詳細資訊，請參閱[MSBuild 專案檔中的保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。 <xref:EnvDTE80.IInternalExtenderProvider>會實作為擷取專案子類型從 automation 擴充項的機制。  
  
 下圖著重於 automation 擴充項實作，專案設定瀏覽物件特別的是，用來擴充基底專案系統專案子類型。  
  
 ![VS 專案類別自動擴充項圖形](../../extensibility/internals/media/vs_projectflavorautoextender.gif "VS_ProjectFlavorAutoExtender")  
專案子類型 Automation 擴充項。  
  
 專案子類型所擴充自動化物件模型，可以進一步擴充基底專案系統。 這些定義為 DTE automation 物件的一部分，而且可用來擴充的專案物件，`ProjectItem`物件和`Configuration`物件。 如需詳細資訊，請參閱[擴充物件模型的基底專案](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。  
  
## <a name="multi-level-aggregation"></a>多層級的彙總  
 包裝較低的層級專案子類型的專案子類型實作需要程式化合作，以允許正常運作的內部專案子類型。 程式設計責任清單包括：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>包裝內部的子類型的專案子類型的實作必須委派給<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>實作內部專案子類型的兩個<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法。  
  
-   <xref:EnvDTE80.IInternalExtenderProvider>包裝函式專案子類型的實作必須於其內部專案子類型的委派。 特別是，實作<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>需要從內部專案子類型取得之名稱的字串，然後再進行串連的字串，它想要加入做為 extender。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>包裝函式專案子類型的實作必須具現化<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>其內部的物件專案子類型，並按住它為私用的委派，因為只有基底專案的專案組態物件直接知道包裝函式專案子類型的組態物件存在。 外部專案子類型可以一開始選擇組態介面，它想要直接處理，然後再委派至內部專案子類型的實作 rest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>。  
  
## <a name="supporting-interfaces"></a>支援的介面  
 基底的專案會委派呼叫，支援專案子類型，新增介面以擴充實作的各種層面。 這包括擴充專案組態的物件和各種屬性瀏覽器物件。 這些介面會擷取藉由呼叫`QueryInterface`上`punkOuter`(指標`IUnknown`) 的最外層的專案子類型的彙總工具。  
  
|介面|專案子類型|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|可讓專案子類型：<br /><br /> 提供的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>。<br />-藉由使用專案子類型，提供自己的實作控制偵錯工具啟動<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。<br />-停用設計階段運算式評估藉由適當地處理`DBGLAUNCH_DesignTimeExprEval`案例在實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>。|  
|<xref:EnvDTE80.IInternalExtenderProvider>|可讓專案子類型：<br /><br /> 擴充<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>来新增或移除組態獨立專案屬性的專案。<br />擴充的專案 automation 物件 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>) 的專案。<br /><br /> 上述的屬性值取自<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列舉型別。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|可讓專案子型別對應回<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>物件指定的專案設定瀏覽的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|可讓專案子型別對應回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>或`VSITEMID`指定專案設定瀏覽物件的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|允許將專案檔 （.vbproj 或.csproj） 任意結構化的 XML 資料保存的專案子類型。 這項資料看不到 MSBuild。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|可讓專案子類型：<br /><br /> 新增新的 MSBuild 屬性，以保存。<br />-從 MSBuild 中移除不必要的屬性。<br />MSBuild 屬性的目前值的查詢。<br />-變更 MSBuild 屬性的目前值。|  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>