---
title: "專案模型的核心元件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project models, objects and interfaces
- project models, services
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7759a2394f2cda19f875a85a22c4a674fee8964
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-model-core-components"></a>專案模型的核心元件
在專案模型上，展開下列資料表。 這些表格顯示介面，而且模型的介面和特定物件相關聯的服務中識別的服務的簡短的描述。 此外，資料表會詳細說明中的專案建立和維護，根據您的特定專案類型的需求是選用的其他介面。  
  
 如需詳細資訊，請參閱[支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)。  
  
### <a name="package-object"></a>封裝物件  
  
|介面|註解|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|初始化 VSPackage 在 IDE 中的，並提供服務給 IDE。|  
  
### <a name="project-factory-object"></a>專案 Factory 物件  
  
|介面|註解|  
|---------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|管理建立新的專案，並開啟現有專案。|  
  
### <a name="project-objects"></a>專案物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|管理的新增和移除專案項目、 開啟編輯器，以及維護每個文件 moniker 之間對應而`VSITEMID`。 繼承自`IVsProject`和`IVsProject2`。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|管理導覽和顯示的屬性，並提供事件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|可讓命令執行類似的`IOleCommandTarget`例如剪下] 和 [重新命名適用於僅當焦點是在 [方案總管] 中的命令。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|做為專案階層架構的主要命令目標介面。 這是標準的介面來查詢其狀態或狀態和執行命令的物件。 當您未在 [專案] 視窗中放置焦點時可用。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|協調的專案狀態的持續性。 一般而言，專案狀態會儲存為專案檔，但不是以檔案為基礎的儲存體系統，可調整。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|可讓專案管理其專案項目，為磁碟或其他儲存體系統中的物件上的檔案的持續性的所有層面。 `IVsPeristHierarchyItem2`介面用於項目不會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|協調原始程式碼控制之間的互動。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|可讓專案管理設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|管理專案組態的物件，例如偵錯/發行組態。 建置、 部署和偵錯作業是透過專案組態的物件。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|藉由控制 （破壞性） 刪除或移除的項目階層的 （非破壞性） 選項的階層。 在呼叫查詢介面`IVsHierarchyDeleteHandler`介面從`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|提供具有支援之物件的實作選項`IVsCfgProvider2`上不同的 COM 識別與專案物件實作的介面`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|選擇性的介面，由其他開發人員實作進行可延伸您的專案。 `IVsProjectStartupServices`介面可讓協力廠商 VSPackage 也可以註冊一個 GUID，您將保存您的專案檔以便每次您的專案載入時，您將您的專案檔案與呼叫載入協力廠商服務 GUID`QueryService`的 GUID。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|藉由在來源階層`UIHierarchy`協調剪貼簿流作業，例如剪下、 複製和貼上的視窗。 使用`AdviseClipboardHelperEvents`介面，以註冊事件剪貼簿。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|提供 UI 階層視窗中拖放作業期間拖曳的項目相對於其資料來源的相關資訊。 從呼叫`IVsHierarchy`介面。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|提供 UI 階層視窗中拖放作業期間拖曳的項目相對於其置放目標的相關資訊。 從呼叫`IVsHierarchy`介面。|  
  
### <a name="configuration-object"></a>組態物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|提供有關組態的資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|可讓專案管理設定資訊。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|可讓專案的偵錯工具控制下執行。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|藉由執行其他專案的部署作業的部署專案。|  
  
### <a name="configuration-builder-object"></a>設定產生器物件  
  
|介面|註解|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|管理專案組態的建立作業。|  
  
### <a name="additional-project-objects"></a>其他專案物件  
  
|介面|註解|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|項目中的屬性顯示**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|顯示部署的輸出。|  
  
 下表顯示專案模型中所識別的服務的簡短描述。  
  
### <a name="services"></a>服務  
  
|服務|註解|  
|-------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|使用 Vspackage 實作專案類型來登錄其專案 factory 存在和 IDE。 VSPackage 必須呼叫`QueryService`這個服務，並註冊其專案 factory 時`IVsPackage::SetSite`方法呼叫。 如果`SetSite`不會呼叫方法，您的專案未具現化。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|提供存取目前的方案，例如列舉專案，建立新的專案中，注意專案變更等的功能的 IDE 的內部、 內建概念。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|呼叫想要參與原始檔控制的專案。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|會維持開啟的文件，以判斷是否一或多個專案項目已開啟的資料表。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|包含介面和方法，呼叫以實際開啟專案項目使用標準編輯器或特定的編輯器。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|所需的所有專案加入、 移除或重新命名其項目時呼叫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|管理變更檔案或目錄，並在磁碟上已經變更選取的檔案時，通知用戶端。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|需要先它們已變更的項目，或將它們儲存所有專案和編輯器所呼叫。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|管理專案組態的組建和部署作業的順序。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|提供用於大多數的偵錯控制項的低層級偵錯工具服務的存取權。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|可讓 VSPackages 存取目前選取項目相關資訊，並能夠啟用與通訊**屬性**視窗。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|提供基本的 UI 相關 IDE 功能，例如建立和列舉工具視窗或文件視窗，或是向使用者回報錯誤。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|提供 IDE 的 [狀態] 列的存取。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|用來實作 automation 模型。 在專案模式中，您將傳回的內容物件，可讓您建立該物件的執行個體。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|用於剪貼簿事件物件上實作專案階層架構中。 `SVsUIHierWinClipboardHelper`可讓您正確地控制代碼剪下、 複製和貼上作業。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [檢查清單： 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [不在組建中： 使用 HierUtil7 專案類別來實作的專案型別 （c + +）](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [支援的符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [專案模型的元素](../../extensibility/internals/elements-of-a-project-model.md)