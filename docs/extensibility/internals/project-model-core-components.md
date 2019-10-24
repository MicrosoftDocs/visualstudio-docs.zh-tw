---
title: 專案模型核心元件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e84438aa57492e28c4e8debc8c1c54e5f496eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725734"
---
# <a name="project-model-core-components"></a>專案模型的核心元件
下表會展開專案模型。 這些資料表會顯示模型中所識別介面和服務的簡短描述，以及與特定物件相關聯的介面和服務。 此外，根據您特定專案類型的需求，資料表會詳細說明在專案建立和維護時選擇性的其他介面。

 如需詳細資訊，請參閱[支援符號流覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。

### <a name="package-object"></a>Package 物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化 IDE 中的 VSPackage，並使其服務可供 IDE 使用。|

### <a name="project-factory-object"></a>Project Factory 物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|管理建立新專案和開啟現有專案。|

### <a name="project-objects"></a>專案物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理專案專案的新增和移除、開啟編輯器，並維護每個檔標記和 `VSITEMID` 之間的對應。 繼承自 `IVsProject` 和 `IVsProject2`。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理導覽和顯示內容，並提供事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|啟用類似于 `IOleCommandTarget` 的命令執行，這類命令僅適用于方案總管的焦點時套用的剪下和重新命名。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|作為專案階層的主要命令目標介面。 這是用來查詢物件以取得其命令狀態或狀態和執行命令的標準介面。 當您未將焦點放在 [專案] 視窗中時提供。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調專案狀態的持續性。 一般來說，專案狀態會儲存為專案檔，但可調整為不是以檔案為基礎的儲存系統。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|可讓專案管理其專案專案的所有持續性層面，就像是磁片上的檔案或其他儲存系統中的物件。 @No__t_0 介面用於不會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 介面的專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調與原始程式碼控制的互動。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|可讓專案管理設定資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案設定物件，例如 Debug/Release 設定。 組建、部署和調試作業會透過專案設定物件進行協調。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|由階層執行，以控制階層專案的刪除（破壞性）或移除（非破壞性）選項。 從 `IVsHierarchy` 介面呼叫 `IVsHierarchyDeleteHandler` 介面上的查詢介面。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供的 [執行] 選項，讓物件在不同的 COM 識別上支援 `IVsCfgProvider2` 介面，而不是實作為 `IVsHierarchy` 介面的專案物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|選擇性的介面，可讓其他開發人員擴充您的專案。 @No__t_0 介面可讓協力廠商 VSPackage 註冊您保存在專案檔中的 GUID，以便在每次載入專案時，將協力廠商服務 GUID 載入至您的專案檔，並針對該 GUID 呼叫 `QueryService`。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|由 `UIHierarchy` 視窗中的來源階層執行，以協調剪貼簿作業（例如剪下、複製和貼上）。 使用 `AdviseClipboardHelperEvents` 介面來註冊剪貼簿事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供在 [UI 階層] 視窗中拖放作業期間，相對於其資料來源之拖曳專案的相關資訊。 從 `IVsHierarchy` 介面呼叫。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供在 [UI 階層] 視窗中拖放作業期間，相對於其放置目標之拖曳專案的相關資訊。 從 `IVsHierarchy` 介面呼叫。|

### <a name="configuration-object"></a>Configuration 物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供設定的相關資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|可讓專案管理設定資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|讓專案可以在偵錯工具的控制項下執行。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|由執行其他專案部署作業的部署專案所執行。|

### <a name="configuration-builder-object"></a>Configuration Builder 物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案設定的組建作業。|

### <a name="additional-project-objects"></a>其他專案物件

|介面|註解|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|在 [**屬性**] 視窗中顯示專案屬性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示部署的輸出。|

 下表提供專案模型中所識別之服務的簡短描述。

### <a name="services"></a>服務

|服務|註解|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|由 Vspackage 所使用，其會執行專案類型來註冊其專案 factory 存在於 IDE 中。 您的 VSPackage 必須呼叫此服務的 `QueryService`，並在呼叫 `IVsPackage::SetSite` 方法時註冊其專案 factory。 如果未呼叫 `SetSite` 方法，您的專案就不會具現化。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|可讓您存取目前方案的 IDE 內部內建概念，例如列舉專案、建立新專案、留意專案變更等功能等等。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|由想要參與原始檔控制的專案所呼叫。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|維護已開啟檔的資料表，以判斷是否已開啟一個或多個專案專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含呼叫的介面和方法，以使用標準編輯器或特定編輯器來實際開啟專案專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|當所有專案加入、移除或重新命名其專案時，必須加以呼叫。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理檔案或目錄的變更，並在磁片上的選取檔案已變更時通知用戶端。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|必須先由所有專案和編輯器呼叫，才能使專案變更或儲存它們。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案設定的組建和部署作業順序。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供用於大部分偵錯工具之低層級偵錯工具服務的存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|可讓您 Vspackage 存取目前選取專案的相關資訊，以及啟用與 [**屬性**] 視窗的通訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的 UI 相關 IDE 功能，例如建立和列舉工具視窗或文件視窗，或向使用者回報錯誤的能力。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供 IDE 狀態列的存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用來執行 automation 模型。 在您的專案模型中，您將會傳回屬性物件，讓您建立該物件的實例。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用來在階層中的專案物件上執行剪貼簿事件。 `SVsUIHierWinClipboardHelper` 可讓您正確地處理剪下、複製和貼上作業。|

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [不在組建中：使用 HierUtil7 專案類別來執行專案類型（C++）](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)