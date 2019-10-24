---
title: 專案設定物件 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3321b70b51d194c67f1deee8ed33e240762b16b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725831"
---
# <a name="project-configuration-object"></a>專案組態物件
專案設定物件會管理 UI 的設定資訊顯示。

 ![Visual Studio 專案](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")設定專案設定屬性頁

 專案設定提供者會管理專案設定。 環境和其他封裝：若要取得和取得專案設定的相關資訊，請呼叫附加至專案設定提供者物件的介面。

> [!NOTE]
> 您無法以程式設計方式建立或編輯解決方案設定檔。 您必須使用 `DTE.SolutionBuilder`。 如需詳細資訊，請參閱[解決方案](../../extensibility/internals/solution-configuration.md)設定。

 若要發行要在設定 UI 中使用的顯示名稱，您的專案應該會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>，這會傳回 `IVsCfg` 指標的清單，您可以用來取得設定的顯示名稱，以及要在環境的 UI 中列出的平臺資訊。 作用中的設定和平臺取決於儲存在使用中解決方案設定中的專案設定。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> 方法可用來取出使用中的專案設定。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> 物件可以選擇性地在具有 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> 物件的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 物件上執行，讓您根據標準專案設定名稱來抓取 `IVsProjectCfg2` 物件。

 另一種提供環境和其他專案存取專案設定的方式，是讓專案提供 `IVsCfgProvider2::GetCfgs` 方法的執行，以傳回一或多個設定物件。 專案也可能會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>，這會繼承自 `IVsProjectCfg`，因而從 `IVsCfg`，以提供設定特有的資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 支援平臺，以及新增、刪除和重新命名專案設定的功能。

> [!NOTE]
> 由於 Visual Studio 不再限制為兩個設定類型，處理設定的程式碼不應該使用設定數目的假設來撰寫，也不應該以假設專案只有一個來撰寫。設定必須是「Debug」或「零售」。 這會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> 並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> 過時。

 在從 `IVsGetCfgProvider::GetCfgProvider` 傳回的物件上呼叫 `QueryInterface`，會抓取 `IVsCfgProvider2`。 如果在 `IVsProject3` 專案物件上呼叫 `QueryInterface` 找不到 `IVsGetCfgProvider`，您可以藉由在階層根瀏覽器物件上呼叫 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)` 所傳回物件的 `QueryInterface`，或透過設定的指標來存取設定提供者物件。為 `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)` 傳回的提供者。

 `IVsProjectCfg2` 主要提供組建、debug 和 deployment 管理物件的存取權，並可讓專案自由分組輸出。 @No__t_0 和 `IVsProjectCfg2` 的方法可用來執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> 來管理組建進程，並 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 設定輸出群組的指標。

 專案必須針對其支援的每個設定傳回相同數目的群組，即使群組中包含的輸出數目可能與設定不同。 群組的識別碼資訊（正式名稱、顯示名稱和群組資訊）也必須與專案中的設定相同。 如需詳細資訊，請參閱[輸出的專案](../../extensibility/internals/project-configuration-for-output.md)設定。

 若要啟用偵錯工具，您的設定應該執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>。 `IVsDebuggableProjectCfg` 是由專案所執行的選用介面，可讓偵錯工具啟動設定，並在具有 `IVsCfg` 和 `IVsProjectCfg` 的設定物件上執行。 當使用者想要按 F5 啟動偵錯工具時，環境會呼叫它。

 `ISpecifyPropertyPages` 和 `IDispatch` 會搭配屬性頁使用，以抓取和顯示與設定相關的資訊給使用者。 如需詳細資訊，請參閱[屬性頁](../../extensibility/internals/property-pages.md)。

## <a name="see-also"></a>請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
- [屬性頁](../../extensibility/internals/property-pages.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)