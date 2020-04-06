---
title: 專案設定物件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 001509b56e3bac6a8fd585eb0efe0bd57018acea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706648"
---
# <a name="project-configuration-object"></a>專案組態物件
專案配置物件管理向 UI 顯示配置資訊。

 ![視覺化工作室項目設定](../../extensibility/internals/media/vsprojectcfg.gif "vs 專案Cfg")專案設定屬性頁

 專案配置提供程式管理專案配置。 若要訪問和檢索有關專案配置的資訊,環境和其他包調用附加到專案配置提供程式物件的介面。

> [!NOTE]
> 無法以程式設計方式創建或編輯解決方案配置檔。 您必須使用 `DTE.SolutionBuilder`。 有關詳細資訊,請參考[解決方案設定](../../extensibility/internals/solution-configuration.md)。

 要發表您要設定 UI 中使用的顯示名稱,<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>專案應實現 。 環境調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>,它返回可用於獲取`IVsCfg`要 在環境 UI 中列出的配置和平臺資訊的顯示名稱的指標清單。 活動配置和平臺由存儲在活動解決方案配置中的專案配置決定。 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>可用於檢索活動專案配置。

 物件<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>可以選擇<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>在 物件上與物件一起<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>實現, 以允許您基於規範專案配置`IVsProjectCfg2`名稱檢索 物件。

 向環境和其他專案提供專案配置訪問許可權的另一種方法是,專案提供方法的`IVsCfgProvider2::GetCfgs`實現以返回一個或多個配置物件。 專案還可以實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>,從繼承`IVsProjectCfg`,`IVsCfg`從而從 中繼承 , 以提供特定於配置的資訊。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>支援用於添加、刪除和重新命名專案設定的平臺和功能。

> [!NOTE]
> 由於 Visual Studio 不再局限於兩種配置類型,因此處理配置的代碼不應與配置數量的假設一起編寫,也不應假定只有一個配置的專案必然是調試或零售。 這使得使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>過時。

 呼叫`QueryInterface``IVsGetCfgProvider::GetCfgProvider`從 檢索傳`IVsCfgProvider2`回的物件 。 如果`IVsGetCfgProvider`通過調`QueryInterface``IVsProject3`用 專案物件找不到,則可以`QueryInterface`通過`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`調用 返回的物件的層次結構根瀏覽器物件或通過指向返回的`IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`配置提供程式的指標來訪問配置提供程式物件。

 `IVsProjectCfg2`主要提供對生成、調試和部署管理對象的訪問,並允許專案自由分組輸出。 的方法`IVsProjectCfg``IVsProjectCfg2`可用於<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>實現管理生成過程,<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>以及配置的輸出組的指標。

 項目必須為其支援的每個配置返回相同數量的組,即使組中包含的輸出數可能因配置而異。 從專案中的配置到配置,組還必須具有相同的標識符資訊(規範名稱、顯示名稱和組資訊)。 有關詳細資訊,請參閱[輸出的項目設定](../../extensibility/internals/project-configuration-for-output.md)。

 要開啟除錯,您的設定應實<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>作 。 `IVsDebuggableProjectCfg`是項目實現的可選介面,允許除錯器啟動配置,並在配置物件上實現`IVsCfg``IVsProjectCfg`, 當用戶選擇通過按 F5 啟動調試器時,環境將調用它。

 `ISpecifyPropertyPages`並`IDispatch`結合屬性頁向使用者檢索和顯示與配置相關的資訊。 有關詳細資訊,請參閱[屬性頁](../../extensibility/internals/property-pages.md)。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [輸出的專案組態](../../extensibility/internals/project-configuration-for-output.md)
- [屬性頁](../../extensibility/internals/property-pages.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)
