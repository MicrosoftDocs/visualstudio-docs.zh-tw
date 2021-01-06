---
title: Visual Studio 中的工作區 |Microsoft Docs
description: 瞭解 Visual Studio 如何使用工作區來代表開啟資料夾中的檔案集合，包括工作區提供者和服務。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 1ed660a5f52aba548d087b28f7caea4d1966fe45
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876944"
---
# <a name="workspaces"></a>工作區

工作區是 Visual Studio 代表 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)中的任何檔案集合，並以類型表示的方式 <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 。 工作區本身不會瞭解資料夾內檔案的相關內容或功能。 相反地，它會為功能和延伸模組提供一組一般的 Api，以產生和取用其他人可採取行動的資料。 產生者是透過 [Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) 使用不同的匯出屬性來撰寫。

## <a name="workspace-providers-and-services"></a>工作區提供者和服務

工作區提供者和服務會提供資料和功能，以回應工作區的內容。 它們可能會提供內容相關的檔案資訊、原始檔中的符號或組建功能。

這兩個概念都使用 [factory 模式](https://en.wikipedia.org/wiki/Factory_method_pattern) ，且工作區會透過 MEF 匯入。 所有的匯出屬性 `IProviderMetadataBase` 都 `IWorkspaceServiceFactoryMetadata` 可實作為或，但有一些明確的類型，這些類型可用於匯出的類型。

提供者與服務之間的差異在於其與工作區的關聯性。 工作區可以有多個特定類型的提供者，但每個工作區只會建立一種特定類型的服務。 例如，工作區有許多檔案掃描器提供者，但工作區的每個工作區只有一個索引服務。

另一個主要差異在於提供者和服務的資料耗用量。 工作區是從提供者取得資料的進入點，有幾個原因。 首先，提供者通常會建立一些較窄的資料集。 資料可能是 c # 原始程式檔的符號或 _CMakeLists.txt_ 檔案的組建檔案內容。 工作區將會比對取用者對其中繼資料與要求相符的提供者要求。 其次，某些案例允許許多提供者參與要求，而其他案例則使用具有最高優先順序的提供者。

相反地，擴充功能可以取得的實例，並直接與工作區服務互動。 上的擴充方法 `IWorkspace` 適用于 Visual Studio 所提供的服務，例如 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> 。 您的擴充功能可能會為您延伸模組內的元件提供工作區服務，或供其他擴充功能使用。 取用者應該使用 <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A> 或您在類型上提供的擴充方法 `IWorkspace` 。

>[!WARNING]
> 請勿撰寫與 Visual Studio 衝突的服務。 這可能會導致非預期的問題。

## <a name="disposal-on-workspace-closure"></a>在工作區關閉時處置

關閉工作區時，擴充項可能需要處置但呼叫非同步程式碼。 <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>介面可讓您輕鬆撰寫此程式碼。

## <a name="related-types"></a>相關類型

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 是開啟的工作區（例如開啟的資料夾）的中央實體。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> 為每個工作區具現化建立提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> 為每個工作區具現化建立服務。
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 應該在需要于處置期間執行非同步程式碼的提供者和服務上執行。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 提供 helper 方法來存取已知的服務或任意服務。

## <a name="workspace-settings"></a>工作區設定

工作區的 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 服務具有簡單但功能強大的工作區控制。 如需設定的基本總覽，請參閱 [自訂群組建和調試](../ide/customize-build-and-debug-tasks-in-visual-studio.md)程式。

大部分類型的設定 `SettingsType` 都是 _json_ 檔案，例如 _VSWorkspaceSettings.json_ 和 _tasks.vs.js_。

工作區設定的功能是以「範圍」為中心，它們只是工作區中的路徑。 當取用者呼叫時 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> ，會匯總包含所要求路徑和設定類型的所有範圍。 範圍匯總優先順序如下所示：

1. 「本機設定」，通常是工作空間根目錄的 `.vs` 目錄。
1. 要求的路徑本身。
1. 所要求路徑的上層目錄。
1. 所有進一步的父目錄，包括工作區根目錄在內。
1. 在使用者目錄中的「全域設定」。

結果是的實例 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 。 這個物件會保存特定類型的設定，而且可以查詢設定儲存為的索引鍵名稱 `string` 。 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>方法和 <xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions> 延伸方法會預期呼叫者知道所要求之設定值的型別。 因為大部分的設定檔案會保存為 _json_ 檔案，所以許多調用將會使用 `string` 、 `bool` 、 `int` 和這些類型的陣列。 也支援物件類型。 在這些情況下，您可以使用 `IWorkspaceSettings` 自己作為型別引數。 例如：

```json
{
  "intValue": 1,
  "stringValue": "s",
  "boolValue": true,
  "stringArray": [
    "s1",
    "s2"
  ],
  "nestedIWorkspaceSettings": {
    "nestedString": "ns"
  }
}
```

假設這些設定是在使用者的 _VSWorkspaceSettings.js_ 中，則可以將資料存取為：

```csharp
using System.Collections.Generic;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static void ReadSettings(IWorkspace workspace)
{
    IWorkspaceSettingsManager settingsManager = workspace.GetSettingsManager();
    IWorkspaceSettings settings = settingsManager.GetAggregatedSettings(SettingsTypes.Generic);

    // result == WorkspaceSettingsResult.Success
    WorkspaceSettingsResult result = settings.GetProperty("intValue", out int intValue);
    result = settings.GetProperty("stringValue", out string stringValue);
    result = settings.GetProperty("boolValue", out bool boolValue);
    result = settings.GetProperty("stringArray", out string[] stringArray);
    result = settings.GetProperty("nestedIWorkspaceSettings", out IWorkspaceSettings nestedIWorkspaceSettings);
    result = nestedIWorkspaceSettings.GetProperty("nestedString", out string nestedString);

    // Extension method alternative using default values.
    int intValueOrDefault = settings.Property("intValue", /* default */ 42);

    // Missing key. result == WorkspaceSettingsResult.Undefined
    result = settings.GetProperty("missing", out string missing);

    // Wrong type for a key. result == WorkspaceSettingsResult.Error
    result = settings.GetProperty("intValue", out IWorkspaceSettings notSettings);

    // Special ability to union "stringArray" across all scopes.
    IEnumerable<string> allStringArray = settings.UnionPropertyArray<string>("stringArray");
}
```

>[!NOTE]
>這些設定 Api 與命名空間中可用的 Api 無關 `Microsoft.VisualStudio.Settings` 。 工作區設定與主機無關，並使用工作區特定的設定檔案或動態設定提供者。

### <a name="providing-dynamic-settings"></a>提供動態設定

擴充功能可以提供 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider> 。 這些記憶體中的提供者允許延伸模組新增設定或覆寫其他設定。

匯出與 `IWorkspaceSettingsProvider` 其他工作區提供者不同。 Factory 不 `IWorkspaceProviderFactory` 存在，而且沒有特殊的屬性類型。 相反地，請執行 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory> 和使用 `[Export(typeof(IWorkspaceSettingsProviderFactory))]` 。

```csharp
// Common workspace provider factory pattern
[ExportFeatureProvider(some, args, to, export)]
internal class MyProviderFactory : IWorkspaceProviderFactory<IFeatureProvider>
{
     IFeatureProvider CreateProvider(IWorkspace workspace) => new Provider(workspace);
}

// IWorkspaceSettingsProvider pattern
[Export(typeof(IWorkspaceSettingsProviderFactory))]
internal class MySettingsProviderFactory : IWorkspaceSettingsProviderFactory
{
    // 100 is typically the value used by built-in settings providers. Lower value is higher priority.
    int Priority => 100;

    IWorkspaceSettingsProvider CreateSettingsProvider(IWorkspace workspace) => new MySettingsProvider(workspace);
}
```

>[!TIP]
>當實 (如) 傳回的方法時，會傳回的 `IWorkspaceSettingsSource` `IWorkspaceSettingsProvider.GetSingleSettings` 實例， `IWorkspaceSettings` 而不是 `IWorkspaceSettingsSource` 。 `IWorkspaceSettings` 提供在某些設定匯總期間可能有用的詳細資訊。

### <a name="settings-related-apis"></a>設定相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 讀取和匯總工作區的設定。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 取得 `IWorkspaceSettingsManager` 工作區的。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 取得在所有重迭範圍中匯總之指定範圍的設定。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 包含特定範圍的設定。

## <a name="workspace-suggested-practices"></a>工作區建議做法

- 從 `IWorkspaceProviderFactory.CreateProvider` 或類似的 api 傳回物件，以 `Workspace` 在建立時記住其內容。 寫入提供者介面時，預期會在建立時保留此物件。
- 在工作區的「本機設定」路徑中儲存工作區特定的快取或設定。 使用 `Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder` 在 Visual Studio 2017 15.6 版或更新版本中建立檔案的路徑。 若為15.6 版之前的版本，請使用下列程式碼片段：

```csharp
using System.IO;
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Settings;

private static string MakeRootedUnderWorkingFolder(IWorkspace workspace, string relativePath)
{
    string workingFolder = workspace.GetSettingsManager().GetAggregatedSettings(SettingsTypes.WorkspaceControlSettings).Property<string>("WorkingFolder");
    return Path.Combine(workingFolder, relativePath);
}
```

## <a name="solution-events-and-package-auto-load"></a>解決方案事件和套件自動載入

載入的封裝可以執行和叫用 `IVsSolutionEvents7` `IVsSolution.AdviseSolutionEvents` 。 它包含在 Visual Studio 中開啟和關閉資料夾的事件。

UI 內容可以用來自動載入您的封裝。 值為 `4646B819-1AE0-4E79-97F4-8A8176FDD664`。

## <a name="troubleshooting"></a>疑難排解

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage 套件未正確載入

工作區擴充性是以 MEF 為基礎，而撰寫錯誤會導致封裝裝載開啟資料夾無法載入。 例如，如果延伸模組使用來匯出型別 `ExportFileContextProviderAttribute` ，但是型別只 `IWorkspaceProviderFactory<IFileContextActionProvider>` 會執行，則嘗試在 Visual Studio 中開啟資料夾時會發生錯誤。

::: moniker range="vs-2017"

您可以在 _%localappdata%\microsoft\visualstudio\ 15.0_Id \componentmodelcache\microsoft.visualstudio.default.err_ 中找到錯誤詳細資料。 針對您的延伸模組所實的類型解決任何錯誤。

::: moniker-end

::: moniker range=">=vs-2019"

您可以在 _%localappdata%\microsoft\visualstudio\ 16.0_Id \componentmodelcache\microsoft.visualstudio.default.err_ 中找到錯誤詳細資料。 針對您的延伸模組所實的類型解決任何錯誤。

::: moniker-end

## <a name="next-steps"></a>後續步驟

* 檔案內容-檔案內容提供者會為開啟資料夾工作區[帶來程式碼](workspace-file-contexts.md)智慧。
* [編制索引](workspace-indexing.md) -工作區索引會收集和保存工作區的相關資訊。
