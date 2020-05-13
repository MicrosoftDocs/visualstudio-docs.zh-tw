---
title: 項目子類型設計 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, design
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b939d197bfd7e58b555ca7698f08643e3d38ef2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706452"
---
# <a name="project-subtypes-design"></a>設計專案子類型

專案子類型允許 VS 套件基於 Microsoft 構建引擎 (MSBuild) 擴展專案。 使用聚合可以重用在中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實現的大部分核心託管項目系統,但仍為特定方案自定義行為。

 以下主題詳細介紹了專案子類型的基本設計和實現:

- 專案子類型設計。

- 多級聚合。

- 支援介面。

## <a name="project-subtype-design"></a>專案子類型設計

通過聚合主<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>類型<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>和 物件來實現專案子類型的初始化。 此聚合使專案子類型能夠覆蓋或增強基礎專案的大部分功能。 專案子類型獲得使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>處理 屬性的第一次機會<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>,使用和<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>命令 使用和和以及使用專案項管理。 專案子類型還可以擴展:

- 專案配置物件。

- 與配置相關的物件。

- 與配置無關的瀏覽物件。

- 專案自動化物件。

- 專案自動化屬性集合。

有關過濾器中, 請參考[專案子型態擴充的屬性與方法](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)。

### <a name="policy-files"></a>原則檔

該[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境提供了一個範例,在策略文件實現中使用專案子類型擴展基礎專案系統。 策略檔案透過管理包括解決方案資源管理員、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**添加專案**對話框、**添加新專案**對話框和 **「屬性」** 對話框的功能,允許塑造環境。 策略子類型通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>重寫和增強這些功能,並`IOleCommandTarget`通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>和實現。

### <a name="aggregation-mechanism"></a>聚合機制

環境的專案子類型聚合機制支援多個級別的聚合,從而允許通過進一步調味項目實現高級子類型。 此外,專案子類型的支援物件(如<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>)旨在允許多層分層。 為了符合 COM 和 COM 聚合規則的約束,需要協同程式設計專案子類型和基礎專案,以使內部子類型或基礎專案能夠正確參與委派方法調用和管理引用計數。 也就是說,要聚合的項目必須程式設計以支援聚合。

下圖顯示了多級專案子類型聚合的原理圖表示形式。

![Visual Studio 多層 projectflavor 圖形](../../extensibility/internals/media/vs_multilevelprojectflavor.gif)

多級專案子類型聚合由三個級別組成,一個基礎專案,由專案子類型聚合,然後由高級專案子類型進一步聚合。 該圖重點介紹了作為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案子類型體系結構的一部分提供的一些支援介面。

### <a name="deployment-mechanisms"></a>部署機制

專案子類型增強的許多基礎專案系統功能包括部署機制。 專案子類型通過實現通過調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg><xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>上的 QueryInterface 檢索的配置介面(如和 ) 來影響部署機制。 在專案子類型和高級專案子類型都添加不同配置實現的情況下,基礎專案調用`QueryInterface`高級專案子類型。 `IUnknown` 如果內部專案子類型包含基礎專案要求的配置實現,則高級專案子類型將委託給內部專案子類型提供的實現。 作為一種將狀態從一個聚合級別持久化到另一個聚合級別的機制,實現專案<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>子類型的所有級別都用於將非生成相關的 XML 數據保存到專案檔中。 關於詳細資訊,請參閱[MSBuild 專案檔中的持久資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)。 <xref:EnvDTE80.IInternalExtenderProvider>作為從專案子類型檢索自動化擴展器的機制實現。

下圖重點介紹了自動化擴展器實現,特別是專案配置流覽物件,專案子類型用於擴展基礎專案系統。

![VS 專案類別自動擴充項圖形](../../extensibility/internals/media/vs_projectflavorautoextender.gif)

專案子類型可以通過擴展自動化物件模型進一步擴展基礎專案系統。 這些被定義為 DTE 自動化物件的一部分,用於擴展 Project 物件、`ProjectItem`物件和`Configuration`物件。 有關詳細資訊,請參閱[延伸基礎項目的物件模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)。

## <a name="multi-level-aggregation"></a>多級聚合

包裝較低級別專案子類型的專案子類型實現需要協同程式設計,以使內部專案子類型正常運行。 程式設計職責清單包括:

- 包裝<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>內部子類型的專案子類型的實現必須委託給內部專案子類型<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>的 實現。<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A>兩者和<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A>方法。

- 包裝<xref:EnvDTE80.IInternalExtenderProvider>器子類型的實現必須委託給其內部專案子類型的實現。 特別是,<xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A>的 實現需要從內部專案子類型獲取名稱字串,然後串聯它要添加為擴展器的字串。

- 包裝<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>器專案子類型的實現必須實例化其內部專案子類型<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>的物件並將其作為私有委託保留,因為只有基礎專案的專案配置物件直接知道包裝器專案子類型配置物件存在。 外部專案子類型最初可以選擇它要直接處理的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>配置介面,然後將其餘部分委託給內部專案子類型的實現。

## <a name="supporting-interfaces"></a>支援介面

基本專案委託調用專案子類型添加的支援介面,以擴展其實現的各個方面。 這包括擴展專案配置物件和各種屬性瀏覽器物件。 這些介面通過調用`QueryInterface`最外層`punkOuter`專案 子類型聚合`IUnknown`器的 (指向 的指標) 來檢索。

|介面|專案子類型|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|允許項目子型態:<br /><br /> - 提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>的 實現。<br />- 使用允許項目子型態提供其自己的執行來控制除錯器<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>的啟動 。<br />- 停用設計時表示式評估`DBGLAUNCH_DesignTimeExprEval`, 在啟動時適當<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>處理案例 。|
|<xref:EnvDTE80.IInternalExtenderProvider>|允許項目子型態:<br /><br /> -<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>擴展專案的,以添加或刪除項目的設定獨立屬性。<br />- 延伸項目的項目自動化<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtObject>物件 ( ) 。<br /><br /> 上面的屬性值取自<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>枚舉。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|允許專案子類型映射回給定專案配置流<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>覽 物件的物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|允許專案子類型映射回<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>`VSITEMID`或 物件,給定專案配置瀏覽物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|允許專案子類型將任意 XML 結構化資料保存到專案檔 (.vbproj 或 .csproj)。 此數據對 MSBuild 不可見。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|允許項目子型態:<br /><br /> - 添加新的 MSBuild 屬性以持久化。<br />- 從 MSBuild 中刪除不必要的屬性。<br />- 查詢 MSBuild 屬性的當前值。<br />- 更改 MSBuild 屬性的當前值。|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>
