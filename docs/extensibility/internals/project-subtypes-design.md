---
title: 專案子類型設計 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28cc20d00a9846fa119666b01aea2efab3a128ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909373"
---
# <a name="project-subtypes-design"></a>設計專案子類型

專案子類型可讓 Vspackage 擴充 Microsoft Build Engine (MSBuild) 為基礎的專案。 使用彙總可讓您重複使用的受管理的核心專案系統中實作大量[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]但仍然自訂特定案例的行為。

 下列主題將詳細說明的基本設計和實作專案子類型：

- 專案子類型設計。

- 多層級的彙總。

- 支援的介面。

## <a name="project-subtype-design"></a>專案子類型設計

專案子類型的初始設定之後，即可彙總主<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>物件。 此彙總可以覆寫或增強功能的基底專案的大部分專案子類型。 專案子類型有機會先處理使用的屬性<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>，使用的命令<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>並<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>，和專案項目管理使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>。 此外，也可以擴充專案子類型：

- 專案組態的物件。

- 設定相依的物件。

- 設定獨立瀏覽的物件。

- 專案 automation 物件。

- 專案自動化屬性集合。

如需有關專案子類型所擴充性的詳細資訊，請參閱[屬性和方法擴充的專案子類型](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。

### <a name="policy-files"></a>原則檔

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境提供的擴充原則檔案的實作中的專案子類型與基底專案系統的範例。 原則檔可讓的成形[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]藉由管理功能，包括方案總管 中，環境**加入專案** 對話方塊中，**加入新項目** 對話方塊中， **屬性** 對話方塊。 原則的子類型會覆寫，並增強這些功能透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>，`IOleCommandTarget`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>實作。

### <a name="aggregation-mechanism"></a>彙總機制

環境的專案子類型彙總機制支援多個層級的彙總，因此可讓進階實作進一步 flavoring 特定的專案子類型。 此外，支援物件的專案子類型，例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>，設計為允許多個層級的圖層。 標準的 COM 和 COM 的條件約束與彙總規則、 專案子類型和基底的專案需要以合作方式進行程式設計，以啟用內部的子型別或基底的專案適當地參與委派方法呼叫和管理參考計數. 也就是即將要彙總的專案已進行程式設計，以支援彙總。

下圖顯示多層級的專案子類型彙總的結構描述表示法。

![Visual Studio 多層 projectflavor 圖形](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

多層級的專案子類型彙總包含三個層級，基底的專案，這是依專案子類型，彙總，則進一步彙總進階的專案子類型。 圖著重於支援介面的一部分所提供的一些[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案子類型的架構。

### <a name="deployment-mechanisms"></a>部署機制

基底專案系統的許多功能增強的專案子類型包括部署機制。 專案子類型會影響部署機制，藉由實作組態介面 (例如<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>並<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>)，藉由上呼叫 QueryInterface 擷取<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>。 在此案例中的專案子類型和進階的專案子類型新增不同的設定實作，呼叫基底的專案`QueryInterface`上的進階的專案子類型`IUnknown`。 如果內部專案子類型包含基底的專案要求的設定實作，進階的專案子類型會委派給內部專案子類型所提供的實作。 專案子類型的所有層級實作來保存從一個彙總層級的狀態到另一種機制，<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>保存非建置相關的專案檔的 XML 資料。 如需詳細資訊，請參閱 < [MSBuild 專案檔中的保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。 <xref:EnvDTE80.IInternalExtenderProvider> 會實作為一種機制來擷取專案子類型的 automation 擴充項。

下圖著重於 automation 擴充項實作，專案設定瀏覽物件特別的是，用來擴充基底專案系統專案子類型。

![VS 專案類別自動擴充項圖形](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

專案子類型可以藉由擴充自動化物件模型，進一步擴充基底專案系統。 這些定義為 DTE automation 物件的一部份，而且可用來擴充專案物件，`ProjectItem`物件和`Configuration`物件。 如需詳細資訊，請參閱[擴充物件模型的基底專案](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。

## <a name="multi-level-aggregation"></a>多層級的彙總

包裝一個較低的層級的專案子類型的專案子類型實作需要以合作方式進行程式設計，以允許內部專案子類型，才能正確運作。 程式設計責任清單包括：

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>正在包裝的內部的子類型的專案子類型的實作必須委派給<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>內部的專案子類型的實作，同時<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法。

- <xref:EnvDTE80.IInternalExtenderProvider>包裝函式專案子類型的實作必須委派，其內部的專案子類型。 特別是，實作<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>必須獲得內部專案子類型之名稱的字串，然後再進行串連它想要新增為擴充項的字串。

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>包裝函式專案子類型的實作必須具現化<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>物件，其內部的專案子類型，並容納它做為私用的委派，因為只有基底專案的專案組態物件直接知道包裝函式專案子類型的組態物件存在。 外部專案子類型可以一開始，選擇其想要直接處理的組態介面，然後委派到內部的專案子類型的實作 rest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>。

## <a name="supporting-interfaces"></a>支援的介面

基底的專案會將委派支援加入專案子類型的介面來擴充它的實作的各種層面的呼叫。 這包括擴充專案組態的物件和各種屬性瀏覽器物件。 這些介面藉由呼叫擷取`QueryInterface`上`punkOuter`(指標`IUnknown`) 的最外層的專案子類型的彙總工具。

|介面|專案子類型|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|可讓專案子類型：<br /><br /> -提供的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>。<br />-藉由使用專案子類型，提供它自己的實作控制偵錯工具啟動<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。<br />-停用設計階段運算式評估藉由適當地處理`DBGLAUNCH_DesignTimeExprEval`案例的實作中<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>。|
|<xref:EnvDTE80.IInternalExtenderProvider>|可讓專案子類型：<br /><br /> 擴充<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>来新增或移除組態的專案的獨立屬性的專案。<br />擴充專案自動化物件 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>) 的專案。<br /><br /> 上述的屬性值取自<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>列舉型別。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|可讓專案子類型，對應回<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>指定專案設定瀏覽物件的物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|可讓專案子類型，對應回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>或`VSITEMID`指定專案設定瀏覽物件的物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|可讓專案子類型，將任意結構化的 XML 資料保存到專案檔 （.vbproj 或.csproj）。 這項資料看不到 MSBuild。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|可讓專案子類型：<br /><br /> 新增新的 MSBuild 屬性，以保存。<br />-從 MSBuild 中移除不必要的屬性。<br />-目前的值為 MSBuild 屬性的查詢。<br />-變更為 MSBuild 屬性的目前值。|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>