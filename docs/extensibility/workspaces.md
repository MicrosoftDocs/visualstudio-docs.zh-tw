---
title: 在 Visual Studio 中的工作區 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3489592a-dc0c-4cd3-9b08-cd367626980a
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 4585ebc5288164f9d441c14332a6af0f1142119b
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="workspaces"></a>工作區

工作區是 Visual Studio 如何表示之檔案的任何集合[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)，而由<xref:Microsoft.VisualStudio.Workspace.IWorkspace>型別。 單獨使用時，工作區不了解的內容或資料夾中的檔案與相關的功能。 相反地，它會提供一般的一組 Api 功能和擴充功能來產生並使用其他人可以採取動作的資料。 產生者會透過撰寫[Managed Extensibility Framework](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (MEF) 使用不同匯出屬性。

## <a name="workspace-providers-and-services"></a>工作區提供者和服務

工作區提供者和服務提供的資料和回應內容 工作區的功能。 它們可能會提供內容的檔案資訊、 原始程式檔中的符號，或建置的功能。

這兩個概念使用[原廠模式](https://en.wikipedia.org/wiki/Factory_method_pattern)而且已完成的工作區的 MEF 匯入。 所有的匯出屬性實作`IProviderMetadataBase`或`IWorkspaceServiceFactoryMetadata`，但有擴充功能應該使用的匯出類型的具象類型。

提供者和服務的其中一個差異在於其關聯到工作區。 工作區可以有許多提供者特定的型別，但每個工作區建立特定型別只能有一個服務。 例如，工作區都有許多檔案掃描器的提供者，但工作區都有一個索引服務每個工作區。

另一個主要差異是耗用量的資料提供者和服務。 工作區是從提供者取得資料，基於一些理由的進入點。 首先，提供者通常會有某些窄的他們建立的資料集。 資料可能會是 C# 原始程式檔的符號，或建置的檔案內容_CMakeLists.txt_檔案。 工作區會比對其中繼資料對齊與要求的提供者的取用者要求。 第二，某些情況下讓許多提供者可提供案例的要求，而其他則使用提供者具有高優先順序。

相反地，擴充功能可以取得的執行個體，並直接與工作區的服務互動。 擴充方法`IWorkspace`可供 Visual Studio 所提供，例如服務<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>。 您的擴充功能可能會提供您的擴充功能中的元件或使用其他擴充功能的工作區服務。 取用者應該使用<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetServiceAsync%2A>或您提供的擴充方法`IWorkspace`型別。

>[!WARNING]
> 無法撰寫 Visual Studio 中的衝突的服務。 它可能會導致未預期的問題。

## <a name="disposal-on-workspace-closure"></a>在關閉工作區上的處置

在 closure 中的工作區，extender 可能需要處置，但呼叫非同步程式碼。 <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable>介面可讓撰寫此程式碼輕鬆。

## <a name="related-types"></a>相關的類型

- <xref:Microsoft.VisualStudio.Workspace.IWorkspace> 是像開啟的資料夾開啟的工作區的中央實體。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceProviderFactory`1> 建立每個具現化的工作區提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspaceServiceFactory> 建立每個工作區具現化服務。
- <xref:Microsoft.VisualStudio.Threading.IAsyncDisposable> 應該在提供者和非同步程式碼執行期間處置需要的服務上實作。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper> 提供 helper 方法來存取的已知的服務或任意服務。

## <a name="workspace-settings"></a>工作區設定

工作區擁有<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager>工作區中簡單但強大控制服務。 設定的基本概觀，請參閱[自訂建置和偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)。

設定適用於大部分`SettingsType`類型為_.json_檔，像是_VSWorkspaceSettings.json_和_tasks.vs.json_。

工作區設定的電源中心 「 範圍 」，也就是只在工作區中的路徑。 當取用者呼叫<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A>，包括要求的路徑和設定類型的所有領域會彙都總。 範圍的彙總優先順序如下所示：

1. [本機設定]，這通常是工作區根目錄的`.vs`目錄。
1. 要求的路徑本身。
1. 要求的路徑的父目錄。
1. 所有進一步父目錄，且包含的工作區的根目錄。
1. 全域設定，「 使用者目錄中。

結果是的執行個體<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings>。 此物件保存設定對於特定類型，並可以查詢的索引鍵名稱的設定儲存為`string`。 <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings.GetProperty%2A>方法和<xref:Microsoft.VisualStudio.Workspace.Settings.WorkspaceSettingsExtensions>擴充方法預期的呼叫端知道所要求的設定值的類型。 因為大部分的設定檔會保存為_.json_檔案，許多引動過程將會使用`string`， `bool`， `int`，以及這些類型的陣列。 支援的物件類型。 在這些情況下，您可以使用`IWorkspaceSettings`本身為型別引數。 例如: 

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

假設這些設定是在使用者的_VSWorkspaceSettings.json_，做為可存取的資料：

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
>這些設定的應用程式開發介面不在所提供的 Api 相關`Microsoft.VisualStudio.Settings`命名空間。 工作區設定並不知道主機，並使用工作區專屬的設定檔或動態設定提供者。

### <a name="providing-dynamic-settings"></a>提供動態設定

擴充功能可以提供<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProvider>s。 這些記憶體中的提供者允許加入設定或覆寫其他延伸項目。

匯出`IWorkspaceSettingsProvider`不同於其他工作區提供者。 處理站不`IWorkspaceProviderFactory`並沒有特殊屬性的型別。 相反地，實作<xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsProviderFactory>並用`[Export(typeof(IWorkspaceSettingsProviderFactory))]`。

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
>實作會傳回方法時`IWorkspaceSettingsSource`(像是`IWorkspaceSettingsProvider.GetSingleSettings`)，傳回的執行個體`IWorkspaceSettings`而不是`IWorkspaceSettingsSource`。 `IWorkspaceSettings` 提供一些設定彙總期間可能相當實用的詳細資訊。

### <a name="settings-related-apis"></a>設定相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager> 讀取並彙總的工作區的設定。
- <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetSettingsManager%2A> 取得`IWorkspaceSettingsManager`做為工作區。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettingsManager.GetAggregatedSettings%2A> 取得指定範圍內所有的重疊範圍的彙總資料的設定。
- <xref:Microsoft.VisualStudio.Workspace.Settings.IWorkspaceSettings> 包含針對特定範圍的設定。

## <a name="workspace-suggested-practices"></a>工作區的建議做法

- 傳回物件，從`IWorkspaceProviderFactory.CreateProvider`或類似的 Api，請記住其`Workspace`內容建立時。 必須是此物件會保留在建立寫入提供者介面。
- 儲存特定工作區的快取或工作區的 [本機設定] 的路徑內的設定。 建立檔案使用的路徑`Microsoft.VisualStudio.Workspace.WorkspaceHelper.MakeRootedUnderWorkingFolder`Visual Studio 2017 15.6 或更新版本中。 如需 15.6 版之前的版本中，使用下列程式碼片段：

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

## <a name="solution-events-and-package-auto-load"></a>方案事件和套件自動載入

載入的封裝可以實作`IVsSolutionEvents7`和叫用`IVsSolution.AdviseSolutionEvents`。 它包含在開啟和關閉 Visual Studio 中的資料夾上的事件。

UI 內容可用來自動載入您的封裝。 值為 `4646B819-1AE0-4E79-97F4-8A8176FDD664`。

## <a name="troubleshooting"></a>疑難排解

### <a name="the-sourceexplorerpackage-package-did-not-load-correctly"></a>SourceExplorerPackage 封裝未正確載入

工作區擴充性是大量 MEF 為基礎，並組合錯誤將導致裝載開啟的資料夾，無法載入封裝。 例如，如果延伸模組匯出的類型`ExportFileContextProviderAttribute`，但該型別只實作`IWorkspaceProviderFactory<IFileContextActionProvider>`，嘗試在 Visual Studio 中開啟資料夾時，會發生錯誤。 錯誤詳細資料位於_%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_id\ComponentModelCache\Microsoft.VisualStudio.Default.err_。 解決任何錯誤，以取得您的延伸模組所實作的型別。

## <a name="next-steps"></a>後續步驟

* [檔案內容](workspace-file-contexts.md)-檔案的內容提供者會使程式碼智慧開啟資料夾的工作區。 
* [索引](workspace-indexing.md)-編製索引的工作區會收集並保存的工作區的相關資訊。
