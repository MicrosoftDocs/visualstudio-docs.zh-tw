---
title: 專案模型核心元件 |微軟文件
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
ms.openlocfilehash: 34f65973f0f3edc1dd6264c32d165503dca78681
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706543"
---
# <a name="project-model-core-components"></a>專案模型的核心元件
下表將展開專案模型。 這些表簡要描述了模型中識別的介面和服務以及與特定對象關聯的介面和服務。 此外,這些表還詳細介紹了在專案創建和維護中可選的其他介面,具體取決於特定項目類型的要求。

 有關詳細資訊,請參閱[支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。

### <a name="package-object"></a>套件物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|在 IDE 中初始化 VS 包,並將其服務提供給 IDE。|

### <a name="project-factory-object"></a>專案工廠物件

|介面|註解|
|---------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|管理創建新項目和打開現有專案。|

### <a name="project-objects"></a>專案物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理項目項的添加和刪除,打開編輯器,並維護每個文檔名字項和`VSITEMID`之間的映射。 繼承`IVsProject`與`IVsProject2`。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理導航和顯示屬性並提供事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|啟用類似於命令執行的命令,`IOleCommandTarget`這些命令(如剪切和重命名)僅在焦點位於解決方案資源管理器中時應用。|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|用作專案層次結構的主命令目標介面。 它是查詢物件的命令狀態或狀態和正在運行的命令的標準介面。 當您未在「項目」視窗中集中時可用。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調項目狀態的持久性。 通常,專案狀態存儲為專案檔,但可以適應不基於檔的存儲系統。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|使專案能夠管理其專案項的持久性的所有方面,無論是磁碟上的檔還是其他儲存系統中的物件。 該`IVsPersistHierarchyItem2`介面用於不實現介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>項。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調與原始程式碼控制的互動。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|使項目能夠管理配置資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案配置物件,如調試/釋放配置。 生成、部署和調試操作通過專案配置物件進行協調。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|按層次結構實現,以控制層次結構項的刪除(破壞性)或刪除(非破壞性)選項。 從`IVsHierarchy`介面調用介面上的`IVsHierarchyDeleteHandler`查詢介面。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供實現選項,使支援`IVsCfgProvider2`介面的物件位於不同的 COM 標識上,`IVsHierarchy`而不是實現介面的項目物件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|實現可選的介面,使專案可被其他開發人員擴展。 該`IVsProjectStartupServices`介面使第三方 VSPackage 能夠註冊您儲存到專案檔中的 GUID,以便每次專案載入時,您都會將第三方服務 GUID 載入到`QueryService`專案檔中並呼叫 該 GUID。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|按`UIHierarchy`視窗中的源層次結構實現,以協調剪貼簿操作(如剪切、複製和貼上)。 使用介面`AdviseClipboardHelperEvents`註冊剪貼簿事件。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|在 UI 層次結構視窗中的拖放操作期間,提供有關拖動項相對於其數據源的資訊。 從`IVsHierarchy`介面調用。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|在 UI 層次結構視窗中的拖放操作中提供有關拖動項相對於其放置目標的資訊。 從`IVsHierarchy`介面調用。|

### <a name="configuration-object"></a>設定物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供有關配置的資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|使項目能夠管理配置資訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|使項目能夠在調試器的控制下運行。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|由對其他專案執行部署操作的部署項目實現。|

### <a name="configuration-builder-object"></a>設定產生器物件

|介面|註解|
|----------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案配置的生成操作。|

### <a name="additional-project-objects"></a>其他項目物件

|介面|註解|
|----------------|--------------|
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|在 **「屬性」** 視窗中顯示項目屬性。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示用於部署的輸出。|

 下表簡要描述了專案模型中標識的服務。

### <a name="services"></a>服務

|服務|註解|
|-------------|--------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|VSPackages 用於實現專案類型以註冊其專案工廠是否存在IDE。 VSPackage 必須調`QueryService`用 此服務,並在調用`IVsPackage::SetSite`方法時 註冊其項目工廠。 如果未調用`SetSite`該方法,則不會實例化專案。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供對IDE當前解決方案的內部內建概念的訪問,例如枚舉專案、創建新專案、注意專案更改等。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|由希望參與原始程式碼管理的專案調用。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|維護打開的文檔表,以確定是否已打開一個或多個項目項。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含使用標準編輯器或特定編輯器實際打開專案項而調用的介面和方法。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|所有專案在添加、刪除或重新命名專案時都需要調用它們。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理對檔或目錄的更改,並在磁碟上更改選定檔時通知用戶端。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|要求所有專案和編輯在髒題或保存專案之前調用它們。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案配置的生成和部署操作的順序。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供對用於大多數調試控制件的低級調試器服務的訪問。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|啟用 VSPackages 存取有關目前選擇的資訊,並啟用與 **「屬性」** 視窗的通訊。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供與 UI 相關的基本 IDE 功能,例如創建和枚舉工具視窗或文件視窗或向使用者報告錯誤的能力。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供對 IDE 狀態列的訪問。|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用於實現自動化模型。 在專案模型中,您將傳回屬性物件,該物件允許您創建該物件的實體。|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用於在層次結構中的專案物件上實現剪貼簿事件。 `SVsUIHierWinClipboardHelper`允許您正確處理剪切、複製和貼上操作。|

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [不在產生中:使用 HierUtil7 專案類別 (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [專案模型的項目](../../extensibility/internals/elements-of-a-project-model.md)
