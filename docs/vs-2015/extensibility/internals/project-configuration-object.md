---
title: 專案設定物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 32e4d34ec3d1fbe8753b4185cab76caa77038bd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839111"
---
# <a name="project-configuration-object"></a>專案組態物件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案設定物件可管理對 UI 的設定資訊顯示。  
  
 ![Visual Studio 專案設定](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
專案設定屬性頁  
  
 專案設定提供者會管理專案設定。 環境和其他封裝：若要取得和取得專案設定的相關資訊，請呼叫附加至專案設定提供者物件的介面。  
  
> [!NOTE]
> 您無法以程式設計方式建立或編輯解決方案設定檔。 您必須使用 `DTE.SolutionBuilder`。 如需詳細資訊，請參閱 [方案](../../extensibility/internals/solution-configuration.md) 設定。  
  
 若要發佈要在設定 UI 中使用的顯示名稱，您的專案應該執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> 。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> ，這會傳回指標清單， `IVsCfg` 您可以使用這些指標來取得要在環境的 UI 中列出的設定和平臺資訊的顯示名稱。 作用中的設定和平臺取決於儲存在使用中解決方案設定中的專案設定。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>方法可以用來取得使用中的專案設定。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>您可以選擇性地使用物件，在物件上執行物件， <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> 讓您 `IVsProjectCfg2` 根據標準專案設定名稱來取得物件。  
  
 提供環境和其他專案存取專案設定的另一種方式，是讓專案提供方法的執行 `IVsCfgProvider2::GetCfgs` ，以傳回一或多個設定物件。 專案也可能會在中執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> ，而繼承自 `IVsProjectCfg` 和 `IVsCfg` ，以提供設定特定的資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 支援平臺，以及新增、刪除和重新命名專案設定的功能。  
  
> [!NOTE]
> 由於 Visual Studio 已不再限制為兩個設定類型，因此處理設定的程式碼不應該使用設定數目的假設來撰寫，也不應該在假設只有一個設定的專案必須是 Debug 或 Retail 的情況下撰寫。 這會讓使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> 淘汰。  
  
 呼叫 `QueryInterface` 從抓取傳回的物件 `IVsGetCfgProvider::GetCfgProvider` `IVsCfgProvider2` 。 如果 `IVsGetCfgProvider` 在專案物件上呼叫時找不到 `QueryInterface` `IVsProject3` ，您可以 `QueryInterface` 在階層根瀏覽器物件上，針對所傳回的物件呼叫 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` ，或透過傳回的設定提供者指標，來存取設定提供者物件 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` 。  
  
 `IVsProjectCfg2` 主要會提供組建、偵測和部署管理物件的存取權，並允許專案自由分組輸出。 和的方法 `IVsProjectCfg` `IVsProjectCfg2` 可以用來執行， <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 以管理組建進程，以及設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 輸出群組的指標。  
  
 專案必須針對其支援的每個設定傳回相同的群組數目，即使群組中包含的輸出數目可能會因設定而異。 這些群組也必須具有相同的識別碼資訊 (正式名稱、顯示名稱和群組資訊) 從設定到專案內的設定。 如需詳細資訊，請參閱 [輸出的專案](../../extensibility/internals/project-configuration-for-output.md)設定。  
  
 若要啟用偵錯工具，您的設定應該執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> 。 `IVsDebuggableProjectCfg` 是由專案所執行的選用介面，可讓偵錯工具啟動設定，並使用和在設定物件上 `IVsCfg` 執行 `IVsProjectCfg` 。 當使用者按下 F5 鍵以啟動偵錯工具時，環境就會呼叫它。  
  
 `ISpecifyPropertyPages` 和 `IDispatch` 會搭配屬性頁使用，以抓取和顯示與設定相關的資訊給使用者。 如需詳細資訊，請參閱 [屬性頁](../../extensibility/internals/property-pages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)   
 [組建的專案設定](../../extensibility/internals/project-configuration-for-building.md)   
 [輸出的專案設定](../../extensibility/internals/project-configuration-for-output.md)   
 [屬性頁](../../extensibility/internals/property-pages.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)
