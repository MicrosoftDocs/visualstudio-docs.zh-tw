---
title: 專案模型核心元件 |Microsoft Docs
description: 本文包含專案模型核心中所識別之介面和服務的描述，以及與物件相關聯的介面和服務。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6aeb24b2aee5b0abb3e5d803004ba97725bb707
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876892"
---
# <a name="project-model-core-components"></a>專案模型的核心元件
下表會在專案模型上展開。 這些表格會顯示模型中所識別之介面和服務的簡短描述，以及與特定物件相關聯的介面和服務。 此外，根據特定專案類型的需求，資料表會詳細說明專案建立和維護中的其他介面。

 如需詳細資訊，請參閱 [支援 Symbol-Browsing 工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。

### <a name="package-object"></a>Package 物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化 IDE 中的 VSPackage，並使其服務可供 IDE 使用。|

### <a name="project-factory-object"></a>Project Factory 物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|管理建立新的專案和開啟現有的專案。|

### <a name="project-objects"></a>專案物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理專案專案的新增和移除、開啟編輯器，並維護每個檔的標記和之間的對應 `VSITEMID` 。 繼承自 `IVsProject` 和 `IVsProject2` 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理流覽和顯示內容，並提供事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|啟用命令執行與的類似命令，例如 `IOleCommandTarget` 只有當焦點在方案總管時才適用的剪下和重新命名等命令。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|作為專案階層的主要命令目標介面。 它是用來查詢物件的命令狀態或狀態以及執行命令的標準介面。 當您未將焦點放在 [專案] 視窗時使用。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調專案狀態的持續性。 專案狀態通常會儲存為專案檔，但是可以調整為不是以檔案為基礎的儲存系統。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|可讓專案管理其專案專案的所有持續性層面，例如磁片上的檔案或其他儲存系統中的物件。 `IVsPersistHierarchyItem2`介面是用於不會執行介面的專案 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調與原始程式碼控制的互動。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|可讓專案管理設定資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案設定物件，例如 Debug/Release 設定。 組建、部署和調試作業會透過專案設定物件進行協調。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|由階層所執行以控制刪除 (破壞性) ，或移除階層專案 (非破壞性) 選項。 從介面呼叫介面上的查詢介面 `IVsHierarchyDeleteHandler` `IVsHierarchy` 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供的實選項，是讓支援介面的物件與 `IVsCfgProvider2` 執行介面的專案物件位於不同的 COM 識別上 `IVsHierarchy` 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|選用介面，可讓其他開發人員擴充您的專案。 `IVsProjectStartupServices`介面可讓協力廠商 VSPackage 註冊您保存在專案檔中的 GUID，以便在每次載入專案時，將協力廠商服務 GUID 載入專案檔中，並呼叫 `QueryService` 該 guid。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|由視窗中的來源階層所執行 `UIHierarchy` ，以協調剪貼簿作業，例如剪下、複製和貼上。 使用 `AdviseClipboardHelperEvents` 介面來註冊剪貼簿事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供在 UI 階層視窗中拖放作業期間，相對於其資料來源之已拖曳專案的相關資訊。 從介面呼叫 `IVsHierarchy` 。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供拖曳的專案相對於 UI 階層視窗中拖放作業期間相對於其放置目標的相關資訊。 從介面呼叫 `IVsHierarchy` 。|

### <a name="configuration-object"></a>設定物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供設定的相關資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|可讓專案管理設定資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|讓專案在偵錯工具的控制項下執行。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|由執行其他專案部署作業的部署專案所執行。|

### <a name="configuration-builder-object"></a>Configuration Builder 物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案設定的組建作業。|

### <a name="additional-project-objects"></a>其他專案物件

|介面|註解|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|在 [ **屬性** ] 視窗中顯示專案屬性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示部署的輸出。|

 下表提供專案模型中所識別之服務的簡短描述。

### <a name="services"></a>服務

|服務|註解|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|由執行專案類型的 Vspackage 所使用，以註冊其在 IDE 中存在的專案 factory。 您的 VSPackage 必須呼叫 `QueryService` 此服務，並在呼叫方法時註冊其專案 factory `IVsPackage::SetSite` 。 如果 `SetSite` 未呼叫方法，則不會具現化您的專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供對 IDE 的內部、內建概念的存取權，例如列舉專案、建立新專案、留意專案變更等的能力。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|由想要參與原始檔控制的專案呼叫。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|維護一份開啟的檔，以判斷是否已經開啟一個或多個專案專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含呼叫的介面和方法，以使用標準編輯器或特定編輯器來實際開啟專案專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|當所有專案加入、移除或重新命名其專案時，都必須加以呼叫。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理檔案或目錄的變更，並在磁片上的選取檔案變更時通知用戶端。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|必須先由所有專案和編輯器呼叫，然後才能變更專案或儲存它們。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案設定的組建和部署作業的順序。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供用於大部分偵錯工具之低層級偵錯工具服務的存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|啟用 Vspackage 存取目前選項的相關資訊，並啟用與 [ **屬性** ] 視窗的通訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的 UI 相關 IDE 功能，例如建立和列舉工具視窗或文件視窗，或向使用者回報錯誤的能力。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供 IDE 狀態列的存取權。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用來執行 automation 模型。 在您的專案模型中，您將會傳回可讓您建立該物件之實例的屬性物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用來在階層中的專案物件上執行剪貼簿事件。 `SVsUIHierWinClipboardHelper` 可讓您正確處理剪下、複製和貼上作業。|

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [不在組建中：使用 HierUtil7 專案類別來執行專案類型 (c + +) ](/previous-versions/bb166212(v=vs.100))
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)