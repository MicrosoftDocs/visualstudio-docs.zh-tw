---
title: 專案組態物件 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12e633b3de120d1454e715837f54d4a5222a0137
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245228"
---
# <a name="project-configuration-object"></a>專案組態物件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案組態物件管理 ui 的組態資訊的顯示。  
  
 ![Visual Studio 專案組態](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
專案組態屬性頁  
  
 專案組態提供者管理的專案組態。 環境和其他套件，來取得存取權以及擷取有關專案組態的資訊，請呼叫附加至專案的組態提供者物件的介面。  
  
> [!NOTE]
>  您無法建立，或以程式設計方式編輯方案組態檔。 您必須使用`DTE.SolutionBuilder`。 請參閱[方案組態](../../extensibility/internals/solution-configuration.md)如需詳細資訊。  
  
 若要發行可用於組態 UI 中的顯示名稱，您的專案應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，它會傳回一份`IVsCfg`可用來取得要在環境的 UI 中列出的組態與平台的資訊的顯示名稱的指標。 作用中的組態與平台會取決於專案的組態儲存在使用中的方案組態。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可用來擷取使用中的專案組態。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>物件的類型 （選擇性） 上實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>物件，以允許您擷取`IVsProjectCfg2`物件根據標準的專案組態名稱。  
  
 提供存取權的專案組態中的環境和其他專案的另一種方式為專案提供的實作`IVsCfgProvider2::GetCfgs`方法來傳回一或多個組態物件。 專案也會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，該項則繼承自`IVsProjectCfg`，藉此從`IVsCfg`，以提供特定組態資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 新增、 刪除和重新命名專案組態的支援平台，以及功能。  
  
> [!NOTE]
>  因為 Visual Studio 已不再限制為兩個組態類型，處理組態程式碼寫入時不應該假設使用多少個組態，也不假設應該要撰寫的只有一個專案設定一定是零售或偵錯。 這可讓使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>已經過時。  
  
 呼叫`QueryInterface`傳回的物件上`IVsGetCfgProvider::GetCfgProvider`擷取`IVsCfgProvider2`。 如果`IVsGetCfgProvider`藉由呼叫找不到`QueryInterface`上`IVsProject3`專案物件，您可以藉由呼叫的組態提供者物件`QueryInterface`針對傳回之物件的階層根瀏覽器物件`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`，或透過針對傳回的組態提供者的指標`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`。  
  
 `IVsProjectCfg2` 主要是提供存取，以建置、 偵錯和部署管理物件，並讓專案能夠自由地群組輸出。 方法`IVsProjectCfg`並`IVsProjectCfg2`可以用來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>管理建置程序和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>組態的輸出群組的指標。  
  
 專案必須傳回相同數目的每個組態，它支援即使群組內所包含的輸出數目可能會不同組態設定的群組。 群組必須也有相同的識別項資訊 （正式名稱、 顯示名稱和群組資訊） 組態設定在專案中。 如需詳細資訊，請參閱 <<c0> [ 輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)。  
  
 若要啟用偵錯，您的設定應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。 `IVsDebuggableProjectCfg` 是選擇性的介面實作的專案，以允許偵錯工具啟動的組態和設定物件上實作`IVsCfg`和`IVsProjectCfg`。 當使用者選擇按 f5 鍵啟動偵錯工具時，環境會呼叫它。  
  
 `ISpecifyPropertyPages` 和`IDispatch`可搭配屬性頁來擷取，並向使用者顯示組態相關資訊。 如需詳細資訊，請參閱 <<c0> [ 屬性頁](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)   
 [屬性頁](../../extensibility/internals/property-pages.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)

