---
title: 專案子類型設計 |Microsoft Docs
description: 瞭解專案子類型如何讓 Vspackage 根據 Microsoft Build Engine (MSBuild) 來擴充專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfc689705d4d42016f184a25b70564591aa5c04d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064497"
---
# <a name="project-subtypes-design"></a>設計專案子類型

專案子類型可讓 Vspackage 根據 Microsoft Build Engine (MSBuild) 來擴充專案。 使用匯總可讓您重複使用中所實行的大量核心 managed 專案系統， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 但仍會自訂特定案例的行為。

 下列主題將詳細說明專案子類型的基本設計和實作為：

- 專案子類型的設計。

- 多層級的匯總。

- 支援的介面。

## <a name="project-subtype-design"></a>專案子類型設計

專案子類型的初始化是藉由匯總主要 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 和物件來達成 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> 。 此匯總可讓專案子類型覆寫或增強基底專案的大部分功能。 專案子類型可讓您使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 、使用和的命令， <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 以及使用的專案專案管理來取得處理屬性的第一次機會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> 。 專案子類型也可以擴充：

- 專案設定物件。

- 與設定相依的物件。

- 設定獨立的流覽物件。

- 專案自動化物件。

- 專案自動化屬性集合。

如需有關專案子類型擴充性的詳細資訊，請參閱 [專案子類型所擴充的屬性和方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。

### <a name="policy-files"></a>原則檔

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境提供一個範例，說明如何在其原則檔的執行中，以專案子類型來擴充基底專案系統。 原則檔可讓您 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 管理包含方案總管、[新增 **專案** ] 對話方塊、[ **加入新專案** ] 對話方塊和 [ **屬性** ] 對話方塊的功能，來塑造環境。 原則子類型會透過、和實作為覆寫和增強這些功能 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> `IOleCommandTarget` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 。

### <a name="aggregation-mechanism"></a>匯總機制

環境的專案子類型匯總機制支援多個匯總層級，因此可讓您進一步 flavoring flavored 專案來實作為先進的子型別。 此外，專案子類型的支持對象（例如 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> ）是設計來允許多層級的分層。 為了保持 COM 和 COM 匯總規則的限制，必須以合作方式編寫專案子類型和基底專案的程式設計方式，才能讓內部子類型或基底專案適當地參與委派方法呼叫和管理參考計數。 也就是說，要匯總的專案必須設計成支援匯總。

下圖顯示多層級專案子類型匯總的示意標記法。

![Visual Studio 多層 projectflavor 圖形](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

多層級的專案子類型匯總包含三個層級，也就是基底專案，由專案子類型匯總，然後再以 advanced 專案子類型進一步匯總。 此圖著重于一些在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案子類型架構中提供的支援介面。

### <a name="deployment-mechanisms"></a>部署機制

專案子類型所增強的許多基底專案系統功能，都是部署機制。 專案子類型會藉由執行設定介面來影響部署機制 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> ， (例如，以及藉 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 由呼叫中的 QueryInterface 來抓取) <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 。 在專案子類型和 advanced 專案子類型的案例中，會新增不同的設定實作為基底專案，會呼叫 `QueryInterface` advanced 專案子類型的 `IUnknown` 。 如果內部專案子類型包含基底專案要求的設定執行，則 advanced project 子類型會委派給內部專案子類型所提供的實作為。 作為將狀態從某個匯總層級保存到另一個匯總層級的機制，會執行所有層級的專案子類型， <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 以將非組建相關的 XML 資料保存在專案檔中。 如需詳細資訊，請參閱在 [MSBuild 專案檔中保存資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。 <xref:EnvDTE80.IInternalExtenderProvider> 會實作為從專案子類型取出 automation 擴充項的機制。

下圖著重于自動化擴充項的實作為專案子類型所使用的專案設定流覽物件，以擴充基底專案系統。

![VS 專案類別自動擴充項圖形](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

專案子類型可延伸 automation 物件模型，進一步擴充基底專案系統。 這些定義為 DTE automation 物件的一部分，可用來擴充專案物件、 `ProjectItem` 物件和 `Configuration` 物件。 如需詳細資訊，請參閱 [擴充基底專案的物件模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。

## <a name="multi-level-aggregation"></a>多層級匯總

包裝較低層級專案子類型的專案子類型執行需要以合作方式進行程式設計，以便讓內部專案子類型能夠正常運作。 程式設計職責的清單包括：

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>包裝內部子類型的專案子類型的實，必須委派給 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 和方法的內部專案子類型的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> 。

- 包裝函式 <xref:EnvDTE80.IInternalExtenderProvider> 專案子類型的執行必須委派給其內部專案子類型的。 尤其是，的執行 <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> 需要從內部專案子類型取得名稱的字串，然後串連要加入作為擴充項的字串。

- 包裝函式 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 專案子類型的執行必須具現化 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> 其內部專案子類型的物件，並將其保存為私用委派，因為只有基底專案的專案設定物件才會直接知道包裝函式專案子類型設定物件存在。 外部專案子類型一開始可以選擇要直接處理的設定介面，然後將其餘部分委派給內部專案子類型的實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A> 。

## <a name="supporting-interfaces"></a>支援介面

基底專案會將呼叫委派給專案子類型所加入的支援介面，以擴充其執行的各個層面。 這包括擴充專案設定物件和各種屬性瀏覽器物件。 這些介面是藉由 `QueryInterface` 在 `punkOuter` `IUnknown` 最外層專案子類型匯總工具) 的指標上呼叫 (取出。

|介面|專案子類型|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|允許專案子類型：<br /><br /> -提供的實 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 。<br />-允許專案子類型提供本身的實作為，以控制偵錯工具的啟動 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 。<br />-在其實值中適當地處理案例，以停用設計時程表達式評估 `DBGLAUNCH_DesignTimeExprEval` <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A> 。|
|<xref:EnvDTE80.IInternalExtenderProvider>|允許專案子類型：<br /><br /> -擴充專案的， <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject> 以加入或移除專案的設定獨立屬性。<br />-擴充專案自動化物件 (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject> 專案) 。<br /><br /> 上述的屬性值取自 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 列舉。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|允許專案子類型與 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> 指定的專案設定流覽物件對應回物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|允許專案子類型對應回 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 或 `VSITEMID` 物件（指定專案設定流覽物件）。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|允許專案子類型將任意的 XML 結構化資料保存到專案檔 ( vbproj 或 .csproj) 。 MSBuild 看不到這項資料。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|允許專案子類型：<br /><br /> -新增要保存的 MSBuild 屬性。<br />-從 MSBuild 移除不必要的屬性。<br />-查詢 MSBuild 屬性的目前值。<br />-變更 MSBuild 屬性的目前值。|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
