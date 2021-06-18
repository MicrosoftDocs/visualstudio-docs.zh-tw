---
title: Visual Studio 2022 預覽中移除的 Api
description: 瞭解在 Visual Studio 2022 Preview 中移除的 VS SDK Api，以供延伸模組作者更新其擴充功能以使用 Visual Studio 2022 Preview。
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: bed8d0a261f70acb5e842ebeaf0059faae3fc478
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308689"
---
# <a name="visual-studio-2022-sdk-removed-apis"></a>Visual Studio 2022 SDK 已移除 Api

[!INCLUDE [preview-note](../includes/preview-note.md)]

下列 Api 已從 Visual Studio SDK 移除，而且無法再使用，如需如何更新程式碼的詳細資訊，請參閱每一節。

* [`IVsImageService`](#ivsimageservice)
* [`IBlockContextProvider`](#iblockcontextprovider)
* [`IToolTipProvider`](#itooltipprovider)
* [`IVsTextScanner` 和 `IVsFullTextScanner`](#ivstextscanner-and-ivsfulltextscanner)
* [非同步解決方案載入和輕量解決方案載入](#asynchronous-solution-load-and-lightweight-solution-load)
* [`IVsDummy`](#ivsdummy)
* [`Microsoft.VisualStudio.Shell.Task`](#microsoftvisualstudioshelltask)
* [從來源安全開啟](#open-from-source-safe)
* [適用于 .NET Framework 的新 WPF XAML 設計工具](#new-wpf-xaml-designer-for-net-framework)

## <a name="ivsimageservice"></a>IVsImageService

在 `IVsImageService` Visual Studio 2022 中將會移除。 所有的使用者都 `IVsImageService` 應該改為移至 `IVsImageService2` 。

### <a name="recommended-updates"></a>建議的更新

如果您使用 `IVsImageService` ，請將對對等方法的呼叫取代為對等的呼叫 `IVsImageService2` ：

| **IVsImageService 方法** | **對等的 IVsImageService2 方法** |
|----------------------------|----------------------------------------|
| 加                        | AddCustomImage                         |
| Get                        | GetImage                               |
| GetIconForFile             | GetImageMonikerForFile                 |
| GetIconForFileEx           | GetImageMonikerForFile                 |

`IVsImageService`的 Add 和 Get 方法會依名稱參考自訂影像， (字串) ，而不是使用標記。  建議您最好將程式碼切換成隻使用名字標記來參考自訂影像，但如果這項證明不切實際， `IVsImageService2` 有幾個方法可讓您將名稱與名字相關聯：

* `TryAssociateNameWithMoniker`
* `GetImageMonikerForName`

您可以使用這兩種方法，依名稱繼續參考影像。

## <a name="iblockcontextprovider"></a>IBlockCoNtextProvider

`IBlockContextProvider`和相關類型將在 Visual Studio 2022 中移除。 所有的使用者都 `IBlockContextProvider` 應該改為移至 `IStructureContextSourceProvider` 。

### <a name="recommended-updates"></a>建議的更新

的使用者 `IBlockContextProvider` 應該改用 `IStructureContextSourceProvider` ([檔](/dotnet/api/microsoft.visualstudio.text.adornments.istructurecontextsourceprovider)) 。

## <a name="itooltipprovider"></a>IToolTipProvider

`IToolTipProvider`和相關類型將在 Visual Studio 2022 中移除。 所有的使用者都 `IToolTipProvider` 應該改為移至 `IToolTipService` 。

### <a name="recommended-updates"></a>建議的更新

的使用者 `IToolTipProvider` 應該改用 `IToolTipService` ([檔](/dotnet/api/microsoft.visualstudio.text.adornments.itooltipservice)) 。

## <a name="ivstextscanner-and-ivsfulltextscanner"></a>IVsTextScanner 和 IVsFullTextScanner

`IVsTextScanner` `IVsFullTextScanner` Visual Studio 2022 中已移除和。 或的所有 `IVsTextScanner` 使用者 `IVsFullTextScanner` 都應該改為移至 `IVsTextLines` 。

### <a name="recommended-updates"></a>建議的更新

或的 `IVsTextScanner` 使用者 `IVsFullTextScanner` 應該改用 `IVsTextLines` ([檔](/dotnet/apimicrosoft.visualstudio.textmanager.interop.ivstextlines.getlinetext)) 。

## <a name="asynchronous-solution-load-and-lightweight-solution-load"></a>非同步解決方案載入和輕量解決方案載入

非同步解決方案載入 (ASL) 和輕量解決方案載入 (LSL) 功能已在 Visual Studio 2022 中移除，因為下列方法即將移除：

### <a name="interfaces"></a>介面

* `IVsSolution4` -方法： `IsBackgroundSolutionLoadEnabled` 、 `EnsureProjectsAreLoaded` 、 `EnsureProjectIsLoaded` 、 `EnsureSolutionIsLoaded`
* `IVsSolutionLoadEvents` -方法： `OnBeforeBackgroundSolutionLoadBegins` 、 `OnQueryBackgroundLoadProjectBatch` 、 `OnBeforeLoadProjectBatch` 、 `OnAfterLoadProjectBatch`
* `IVsSolutionLoadManagerSupport` -整個介面
* `IVsSolutionLoadManager` -整個介面
* `IVsSccManager3`  -整個介面
* `IVsAsynchronousProjectCreate` -整個介面
* `IVsAsynchronousProjectCreateUI` -整個介面

### <a name="enums-properties-and-ui-contexts"></a>列舉、屬性和 UI 內容

* `VSHPROPID_ProjectUnloadStatus` 列舉 `UNLOADSTATUS_LoadPendingIfNeeded`
* `VSHPROPID_DemandLoadDependencies`
* `VSHPROPID_IsProjectProvisioned`
* `VSPROPID_IsInBackgroundIdleLoadProjectBatch`
* `VSPROPID_IsInSyncDemandLoadProjectBatch`
* `VSPROPID_ActiveSolutionLoadManager`
* `UICONTEXT_BackgroundProjectLoad`

### <a name="recommended-updates"></a>建議的更新

無。

## <a name="ivsdummy"></a>IVsDummy

將 `IVsDummy` 在 Visual Studio 2022 中移除，且不會被取代。 

### <a name="recommended-updates"></a>建議的更新

無。 但是，它應該不會有任何影響，因為 API 沒有任何作用。

## <a name="microsoftvisualstudioshelltask"></a>VisualStudio。

`Microsoft.VisualStudio.Shell.Task`類別已重新命名為， `Microsoft.VisualStudio.Shell.TaskListItem` 因此不會與非常受歡迎的類別發生衝突 `System.Threading.Tasks.Task` 。

## <a name="open-from-source-safe"></a>從來源安全開啟

已移除從來源安全開啟方案的支援，因為下列方法、事件和都將會移除常數。

## <a name="interfaces"></a>介面

* `IVsSCCProvider3` -整個介面

### <a name="recommended-updates"></a>建議的更新

無。

## <a name="new-wpf-xaml-designer-for-net-framework"></a>適用于 .NET Framework 的新 WPF XAML 設計工具

目前適用于 .NET Framework 的 WPF XAML 設計工具已被取代，並會根據用於適用于 .NET 的 WPF XAML 設計工具 ( .NET Core) 的相同架構，以適用于 .NET Framework 的新 WPF XAML 設計工具取代。 這也表示 WPF .NET Framework 根據 .design.dll 和 Microsoft 設計擴充性模型。不再支援擴充性。 適用于 .NET Framework 的新 WPF XAML 設計工具將提供與 .NET ( .NET Core) 的 WPF XAML 設計工具相同的擴充性模型。 如果您已經建立 .NET ( .NET Core) 的 .designtools.dll 擴充功能，該相同的延伸模組將適用于 .NET Framework 的新 WPF XAML 設計工具。 請參閱下面的遷移連結，以取得有關如何遷移至 WPF 平臺的新擴充性模型 ( .NET Framework 和 .NET Core) 以及 UWP 平臺向前移動的詳細資訊。 

### <a name="recommended-updates"></a>建議的更新

請參閱 [XAML 設計](https://github.com/microsoft/xaml-designer-extensibility/blob/main/documents/xaml-designer-extensibility-migration.md)工具擴充性遷移。
