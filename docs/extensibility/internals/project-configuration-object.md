---
title: "專案組態物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a1b1e7c7b782868ece2c640f75fd506018f3e04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-object"></a>專案組態物件
專案組態物件管理 ui 的組態資訊的顯示。  
  
 ![Visual Studio 專案組態](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
專案組態屬性頁  
  
 專案組態提供者管理的專案組態。 環境和其他封裝，才能存取和擷取有關專案組態的資訊，請呼叫附加至專案的組態提供者物件的介面。  
  
> [!NOTE]
>  您無法建立或編輯的方案組態檔，以程式設計的方式。 您必須使用`DTE.SolutionBuilder`。 請參閱[方案組態](../../extensibility/internals/solution-configuration.md)如需詳細資訊。  
  
 若要發行時要使用的組態 UI 中的顯示名稱，您的專案必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，它會傳回一份`IVsCfg`可用來取得要在環境的 UI 中列出的組態和平台資訊的顯示名稱的指標。 使用中的組態與平台由儲存在使用中的方案組態的專案的組態來決定。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可以用來擷取現用專案組態。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>物件可以選擇性地實作上<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>物件可讓您擷取`IVsProjectCfg2`物件會根據標準的專案組態名稱。  
  
 提供存取權的專案組態的環境和其他專案的另一個方法是讓專案提供的實作`IVsCfgProvider2::GetCfgs`方法以傳回一個或多個組態物件。 專案也會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，後者繼承自`IVsProjectCfg`，藉此從`IVsCfg`，提供特定組態資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>加入、 刪除和重新命名專案組態的支援平台，以及功能。  
  
> [!NOTE]
>  因為 Visual Studio 不再限制為兩個組態類型，處理組態程式碼寫入時不應該假設的大約數目的設定，也不應該則寫入以假設，只有一個專案設定一定是偵錯或零售版。 這可讓使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>過時。  
  
 呼叫`QueryInterface`從傳回的物件上`IVsGetCfgProvider::GetCfgProvider`擷取`IVsCfgProvider2`。 如果`IVsGetCfgProvider`藉由呼叫找不到`QueryInterface`上`IVsProject3`專案物件，您可以存取的組態提供者物件藉由呼叫`QueryInterface`在階層的根瀏覽器物件傳回的物件上`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`，或透過針對傳回的組態提供者的指標`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`。  
  
 `IVsProjectCfg2`主要提供存取建置、 偵錯和部署管理物件，並允許自由群組輸出的專案。 方法的`IVsProjectCfg`和`IVsProjectCfg2`可以用來實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>管理建置程序，和<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>組態的輸出群組的指標。  
  
 專案必須傳回相同數目的群組，即使群組內所包含的輸出數目而異的組態設定，它支援每個組態。 群組必須也有相同的識別元資訊 （正式名稱、 顯示名稱和群組資訊） 組態設定專案中。 如需詳細資訊，請參閱[專案組態輸出](../../extensibility/internals/project-configuration-for-output.md)。  
  
 若要啟用偵錯，您的設定應該實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。 `IVsDebuggableProjectCfg`偵錯工具啟動組態的專案所實作的選擇性介面，且使用的設定物件上實作`IVsCfg`和`IVsProjectCfg`。 當使用者選擇按 f5 鍵啟動偵錯工具時，環境會呼叫它。  
  
 `ISpecifyPropertyPages`和`IDispatch`可用搭配屬性頁來擷取，並向使用者顯示組態相關資訊。 如需詳細資訊，請參閱[屬性頁](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態的輸出](../../extensibility/internals/project-configuration-for-output.md)   
 [屬性頁](../../extensibility/internals/property-pages.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)