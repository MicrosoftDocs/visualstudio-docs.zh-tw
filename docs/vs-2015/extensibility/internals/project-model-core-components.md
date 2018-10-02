---
title: 專案模型的核心元件 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e0fd5b5963686ac38975c62bab1d8ee93224cf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47486350"
---
# <a name="project-model-core-components"></a>專案模型的核心元件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[專案模型的核心元件](https://docs.microsoft.com/visualstudio/extensibility/internals/project-model-core-components)。  
  
下表會探討專案模型。 這些表格會顯示在模型中的介面和特定物件相關聯的服務中所識別的服務與介面的簡短描述。 此外，資料表將詳細說明其他在專案建立及維護，根據您的特定專案類型的需求中是選擇性的介面。  
  
 如需詳細資訊，請參閱 <<c0> [ 支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
### <a name="package-object"></a>封裝物件  
  
|介面|註解|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化 VSPackage 在 IDE 中的，並提供其服務給 IDE。|  
  
### <a name="project-factory-object"></a>Project Factory 物件  
  
|介面|註解|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|建立新的專案和開啟現有的專案管理。|  
  
### <a name="project-objects"></a>專案物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理的新增和移除專案項目，開啟編輯器，並維護每個文件 moniker 之間的對應和`VSITEMID`。 繼承自`IVsProject`和`IVsProject2`。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理瀏覽] 和 [顯示屬性，並提供事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|可讓命令執行類似的`IOleCommandTarget`例如剪下 和 重新命名，適用於僅當焦點是在方案總管 中的命令。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|可作為主要的命令目標介面專案階層架構。 這是標準的介面來查詢其狀態或狀態和執行命令的物件。 當您未在 [專案] 視窗中放置焦點時可用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調，專案狀態的持續性。 一般而言，專案狀態會儲存為專案檔，但可以適用於不是以檔案為基礎的儲存體系統。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|可讓專案，以管理其專案項目，為磁碟或其他儲存體系統中的物件上的檔案持續性的所有層面。 `IVsPeristHierarchyItem2`介面用於不會實作的項目<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調與原始程式碼控制之間的互動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|可讓專案管理設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案組態的物件，例如偵錯/發行組態。 建置、 部署和偵錯作業是透過專案組態的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|藉由階層，以控制刪除 （破壞性），或移除的階層項目 （非破壞性） 的選項。 在呼叫查詢介面`IVsHierarchyDeleteHandler`介面從`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供具有支援之物件的實作選項`IVsCfgProvider2`在不同的 COM 識別專案物件和實作的介面`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|選擇性的介面，由其他開發人員實作以進行可延伸您的專案。 `IVsProjectStartupServices`介面可讓協力廠商 VSPackage 也可以註冊一個 GUID，您將保存您的專案檔以便每次您的專案載入時，您會將第三方服務 GUID 載入您的專案檔和呼叫`QueryService`該 guid。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|藉由將來源階層中`UIHierarchy`協調剪貼簿 作業，例如剪下、 複製和貼上的視窗。 使用`AdviseClipboardHelperEvents`註冊剪貼簿事件的介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供 UI 階層視窗中的拖放作業期間拖曳的項目相對於其資料來源的相關資訊。 從呼叫`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供 UI 階層視窗中的拖放作業期間拖曳的項目相對於其放置目標的相關資訊。 從呼叫`IVsHierarchy`介面。|  
  
### <a name="configuration-object"></a>組態物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供組態資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|可讓專案管理設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|可讓專案在偵錯工具的控制下執行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|藉由執行的其他專案的部署作業的部署專案。|  
  
### <a name="configuration-builder-object"></a>組態產生器物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案組態的建立作業。|  
  
### <a name="additional-project-objects"></a>其他專案物件  
  
|介面|註解|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|顯示項目中的屬性**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示部署的輸出。|  
  
 下表顯示專案模型中所識別之服務的簡短描述。  
  
### <a name="services"></a>服務  
  
|服務|註解|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|使用 Vspackage 實作專案類型來註冊其專案的處理站存在與 IDE。 VSPackage 必須呼叫`QueryService`此服務，並註冊其專案 factory 時`IVsPackage::SetSite`呼叫方法。 如果`SetSite`不會呼叫方法，您的專案未具現化。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供存取權的目前方案中，例如能夠列舉專案、 建立新的專案、 專案的變更，注意等等的 IDE 的內部、 內建概念。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|呼叫所想要參與原始檔控制的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|會維持開啟的文件，以判斷是否一或多個專案項目都已開啟的資料表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含介面和方法呼叫，以實際開啟專案項目使用的標準編輯器或特定的編輯器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|需要新增、 移除或重新命名其項目時，要呼叫的所有專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理變更的檔案或目錄，並通知用戶端，當選取的檔案在磁碟上已經變更。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|需要在已變更的項目，或將它們儲存之前由所有專案和編輯器呼叫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案組態的組建和部署作業的順序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供用於大部分的偵錯控制項的低層級的偵錯工具服務的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|可讓 VSPackages 存取目前選取項目相關資訊，並可讓與通訊**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的 UI 相關的 IDE 功能，例如建立和列舉工具視窗或文件視窗或報告錯誤給使用者的能力。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供 IDE 的 [狀態] 列的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用來實作自動化模型。 在您專案的模型，您將會傳回屬性物件，可讓您建立該物件的執行個體。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用來實作專案物件階層架構中的剪貼簿 的事件。 `SVsUIHierWinClipboardHelper` 可讓您正確地控制代碼剪下、 複製和貼上作業。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在組建中： 使用 HierUtil7 專案類別來實作專案類型 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)

