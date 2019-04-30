---
title: 在 Visual Studio 中的工作區 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 011781b434c4d005e473c5f97c60a9269dc5d034
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952759"
---
# <a name="workspaces"></a>工作區

工作區是 Visual Studio 如何代表任何集合中的檔案[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)，而且它會以表示<xref:Microsoft.VisualStudio.Workspace.IWorkspace>型別。 單獨使用時，工作區並不了解的內容或資料夾中的檔案與相關的功能。 相反地，它會提供一組一般 Api 功能和擴充功能來產生和取用其他人可以立即處理的資料。 產生者是透過組成[Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) 使用各種匯出的屬性。

## <a name="workspace-providers-and-services"></a>工作區提供者和服務

工作區提供者和服務提供的資料和回應的工作區內容的功能。 它們可能會提供內容相關的檔案資訊，請在原始程式檔中的符號，或是建置功能。

使用這兩個概念[factory 模式](https://en.wikipedia.org/wiki/Factory_method_pattern)和透過工作區的 MEF 匯入。 匯出的所有屬性都實作`IProviderMetadataBase`或`IWorkspaceServiceFactoryMetadata`，但有延伸模組應該用於匯出類型的具象類型。

提供者和服務之間的差異之一是其關聯到工作區。 工作區可以有許多提供者特定的類型，但只有一個特定類型的服務會建立每個工作區。 例如，工作區有許多檔案掃瞄器提供者，但工作區具有每個工作區的只有一個編製索引的服務。

另一個主要差異是取用的資料提供者和服務。 工作區是從提供者取得資料，原因如下的進入點。 首先，提供者通常會有一些窄他們建立的資料集。 資料可能的符號C#原始程式檔，或建置的檔案內容_CMakeLists.txt_檔案。 工作區會比對其中繼資料符合要求的提供者的取用者的要求。 第二，某些情況下提供許多參與的要求，而其他案例的提供者會使用提供者以高優先權。

相反地，擴充功能可以取得的執行個體，並直接互動的工作區的服務。 擴充方法`IWorkspace`適用於 Visual Studio 所提供，例如服務<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>。 您的延伸模組可能會提供您的延伸模組內的元件或使用其他擴充功能的工作區服務。 取用者應該使用<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A>或您所提供的擴充方法`IWorkspace`型別。

>[!WARNING]
> 不撰寫 Visual Studio 與衝突的服務。 它可能會導致未預期的問題。

## <a name="disposal-on-workspace-closure"></a>在 工作區關閉處置

在工作區的 closure 中，擴充項可能需要處置，但呼叫非同步程式碼。 <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>介面可讓撰寫這個程式碼。

## <a name="related-types"></a>相關的類型

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 是開啟的工作區，例如開啟的資料夾的中央實體。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> 建立每個具現化的工作區提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> 建立每個具現化的工作區的服務。
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 應該提供者與需要執行非同步程式碼期間可供使用的服務上實作。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 提供 helper 方法來存取的已知的服務或任意服務。

## <a name="workspace-settings"></a>工作區設定

工作區有<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager>簡單但功能強大的控管工作區的服務。 如需設定的基本概觀，請參閱 <<c0> [ 自訂建置與偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)。

設定適用於大部分`SettingsType`類型是 _.json_檔，像是_VSWorkspaceSettings.json_並_tasks.vs.json_。

工作區設定的電源都著重於 「 範圍 」，也就是只在工作區中的路徑。 當取用者呼叫<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>，包括要求的路徑和設定類型的所有範圍會彙都總。 範圍彙總的優先順序如下所示：

1. [本機設定]，這通常是工作區根目錄的`.vs`目錄。
1. 要求的路徑本身。
1. 要求的路徑的上層目錄。
1. 所有進一步父目錄，包括工作區根目錄。
1. [全域設定]，也就是使用者目錄中。

結果是的執行個體<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>。 此物件保存特定類型的設定，而且可在設定索引鍵名稱為預存查詢`string`。 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>方法和<xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions>延伸方法預期呼叫者知道所要求的設定值的型別。 因為大部分的設定檔會保存為 _.json_檔案，將會使用許多的引動過程`string`， `bool`， `int`，以及這些類型的陣列。 支援的物件類型。 在這些情況下，您可以使用`IWorkspaceSettings`本身作為類型引數。 例如: 

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

在使用者的假設這些設定已_VSWorkspaceSettings.json_，可以存取的資料，做為：

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
>這些設定 Api 無關中提供的 Api`Microsoft.VisualStudio.Settings`命名空間。 工作區設定並不知道主機，並使用工作區特有的設定檔或動態設定提供者。

### <a name="providing-dynamic-settings"></a>提供動態設定

延伸模組可以提供<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s。 這些記憶體提供者允許新增設定或覆寫其他擴充功能。

匯出`IWorkspaceSettingsProvider`不同於其他工作區提供者。 處理站不`IWorkspaceProviderFactory`並沒有特殊屬性類型。 請改為實作<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory>並用`[Export(typeof(IWorkspaceSettingsProviderFactory))]`。

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
>實作方法傳回時`IWorkspaceSettingsSource`(例如`IWorkspaceSettingsProvider.GetSingleSettings`)，傳回的執行個體`IWorkspaceSettings`而非`IWorkspaceSettingsSource`。 `IWorkspaceSettings` 提供可用在某些設定彙總期間的詳細資訊。

### <a name="settings-related-apis"></a>設定相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 讀取並彙總工作區的設定。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 取得`IWorkspaceSettingsManager`工作區。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 取得指定範圍，彙總所有的重疊範圍的設定。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 包含特定範圍的設定。

## <a name="workspace-suggested-practices"></a>工作區的建議做法

- 傳回物件，從`IWorkspaceProviderFactory.CreateProvider`或類似的 Api，請記住其`Workspace`時建立的內容。 提供者介面會編寫成需要這個物件會保留在建立。
- 儲存區特定的快取或工作區的 「 本機設定 」 路徑中的設定。 建立您的檔案使用的路徑`Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`Visual Studio 2017 15.6 版或更新版本中。 15.6 版之前的版本，使用下列程式碼片段：

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

## <a name="solution-events-and-package-auto-load"></a>方案事件與封裝自動載入

載入的封裝可實作`IVsSolutionEvents7`，並叫用`IVsSolution.AdviseSolutionEvents`。 它包含在開啟和關閉資料夾，以在 Visual Studio 中的事件。

UI 內容可以用於自動載入您的套件。 值為 `4646B819-1AE0-4E79-97F4-8A8176FDD664`。

## <a name="troubleshooting"></a>疑難排解

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage 封裝未正確載入

工作區擴充性是大量 MEF 為基礎，並撰寫錯誤會造成裝載開啟資料夾，無法載入封裝。 例如，如果延伸模組匯出的型別`ExportFileContextProviderAttribute`，但只會實作類型`IWorkspaceProviderFactory<IFileContextActionProvider>`，嘗試在 Visual Studio 中開啟資料夾時，會發生錯誤。

::: moniker range="vs-2017"

錯誤詳細資料可在 _%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_。 解決任何錯誤，您的延伸模組所實作的型別。

::: moniker-end

::: moniker range=">=vs-2019"

錯誤詳細資料可在 _%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_。 解決任何錯誤，您的延伸模組所實作的型別。

::: moniker-end

## <a name="next-steps"></a>後續步驟

* [檔案內容](workspace-file-contexts.md)-檔案的內容提供者會將程式碼智慧開啟資料夾的工作區。
* [編製索引](workspace-indexing.md)-編製索引的工作區會收集並保存的工作區的相關資訊。
