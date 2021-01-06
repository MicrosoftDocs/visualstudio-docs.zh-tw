---
title: Visual Studio 中的工作區組建 |Microsoft Docs
description: 瞭解為工作區提供索引和檔案內容資料以支援開啟資料夾案例的擴充項。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: e44c2398b873bbca95c971ae1b44ac3de831b2ae
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877100"
---
# <a name="workspace-build"></a>工作區組建

[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)案例中的組建支援需要擴充項來提供[工作區](workspaces.md)的[索引](workspace-indexing.md)和檔案[內容](workspace-file-contexts.md)資料，以及要執行的組建動作。

以下是您的延伸模組所需的大綱。

## <a name="build-file-context"></a>組建檔案內容

- 提供者 factory
  - `ExportFileContextProviderAttribute` 具有 `supportedContextTypeGuids` as 所有適用 `string` 常數的屬性 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 檔案內容提供者
    - `FileContext`針對每個組建作業和支援的設定傳回
      - 來自 <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 的 `contextType`
      - `context`<xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext>使用 `Configuration` 屬性做為組建設定來實 (例如 `"Debug|x86"` ， `"ret"` 或 `null` 不適用) 。 或者，請使用的實例 <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext> 。 設定值 **必須** 符合已編制索引之檔案資料值的設定。

## <a name="indexed-build-file-data-value"></a>已編制索引的組建檔案資料值

- 提供者 Factory
  - `ExportFileScannerAttribute` 具有 `IReadOnlyCollection<FileDataValue>` 做為支援類型的屬性
  - 實作 `IWorkspaceProviderFactory<IFileScanner>`
- 檔案掃描器開啟 `ScanContentAsync<T>`
  - 當 `FileScannerTypeConstants.FileDataValuesType` 是類型引數時傳回資料
  - 針對以下列方式建立的每個設定，傳回檔案資料值：
    - `type` 按照 `BuildConfigurationContext.ContextTypeGuid`
    - `context` 例如，如果您的組建設定 (，則為， `"Debug|x86"` `"ret"` 或者， `null` 如果不適用) ，則為。 此值 **必須** 符合檔案內容中的設定。

## <a name="build-file-context-action"></a>組建檔案內容動作

- 提供者 factory
  - `ExportFileContextActionProvider` 具有 `supportedContextTypeGuids` as 所有適用 `string` 常數的屬性 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextActionProvider>`
- 上的動作提供者 `IFileContextActionProvider.GetActionsAsync`
  - `IFileContextAction`傳回符合指定值的。 `FileContext.ContextType`
- 檔案內容動作
  - Implements `IFileContextAction` 和 <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` 屬性傳回 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` 適用 `0x1000` 于組建、 `0x1010` 重建或 `0x1020` 清除

>[!NOTE]
>由於 `FileDataValue` 需要建立索引，因此開啟工作區和掃描檔案以取得完整組建功能的時間點之間會有一些時間。 因為沒有先前快取的索引，所以第一次開啟資料夾時會出現延遲。

## <a name="reporting-messages-from-a-build"></a>從組建報告訊息

組建可以將資訊、警告和錯誤訊息以兩種方式呈現給使用者。 簡單的方法是使用 <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 並提供 <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage> ，如下所示：

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` 以及 `BuildMessage.LogMessage` 控制將資訊呈現給使用者的行為。 以外 `BuildMessage.TaskType` 的任何值 `None` 都會產生具有指定詳細資料的 **錯誤清單** 專案。 `LogMessage`一律會在 **輸出** 工具視窗的 [**組建**] 窗格中輸出。

或者，擴充功能可以直接與 [ **錯誤清單** ] 或 [ **組建** ] 窗格互動。 Bug 存在於 Visual Studio 2017 15.7 版之前的版本中，其中的 `pszProjectUniqueName` 引數 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> 會被忽略。

>[!WARNING]
>的呼叫端 `IFileContextAction.ExecuteAsync` 可以提供引數的任意基礎 `IProgress<IFileContextActionProgressUpdate>` 實作為。 永遠不會直接叫用 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` 。 目前沒有使用此引數的一般指導方針，但這些指導方針有可能變更。

## <a name="build-related-apis"></a>建立相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 提供組建設定詳細資料。
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService><xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>向使用者顯示。

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.js開啟並 launch.vs.js開啟

如需在檔案上撰寫 tasks.vs.js或 launch.vs.js的詳細資訊，請參閱 [自訂群組建和調試](../ide/customize-build-and-debug-tasks-in-visual-studio.md)程式。

## <a name="next-steps"></a>後續步驟

* [語言伺服器通訊協定](language-server-protocol.md) -瞭解如何將語言伺服器整合至 Visual Studio。