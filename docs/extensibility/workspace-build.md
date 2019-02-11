---
title: Visual Studio 中的工作區組建 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 82660ee772280563b91830aaf1a18da0bc742b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951224"
---
# <a name="workspace-build"></a>組建工作區

支援建置[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)案例需要提供的擴充項[編製索引](workspace-indexing.md)並[檔案內容](workspace-file-contexts.md)資料[工作區](workspaces.md)，做為以及要執行的建置動作。

以下是 概述您的擴充功能需要什麼。

## <a name="build-file-context"></a>建置的檔案內容

- 提供者 factory
  - `ExportFileContextProviderAttribute` 屬性搭配`supportedContextTypeGuids`為所有適用`string`常數 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 檔案內容提供者
    - 傳回`FileContext`每個建置作業和支援的組態
      - `contextType` 從 <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` 會實作<xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext>具有`Configuration`做為組建組態屬性 (例如`"Debug|x86"`， `"ret"`，或`null`如果不適用)。 或者，使用的執行個體<xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>。 組態值**必須**符合從索引的檔案資料值的組態。

## <a name="indexed-build-file-data-value"></a>索引的建置的檔案資料值

- 提供者 Factory
  - `ExportFileScannerAttribute` 屬性與`IReadOnlyCollection<FileDataValue>`為支援的類型
  - 實作 `IWorkspaceProviderFactory<IFileScanner>`
- 上的檔案掃描 `ScanContentAsync<T>`
  - 傳回資料時`FileScannerTypeConstants.FileDataValuesType`是型別引數
  - 傳回建構的每個組態的檔案資料值：
    - `type` 做為 `BuildConfigurationContext.ContextTypeGuid`
    - `context` 為您的組建組態 (例如`"Debug|x86"`， `"ret"`，或`null`如果不適用)。 此值**必須**符合從檔案內容的組態。

## <a name="build-file-context-action"></a>建置的檔案內容動作

- 提供者 factory
  - `ExportFileContextActionProvider` 屬性搭配`supportedContextTypeGuids`為所有適用`string`常數 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextActionProvider>`
- 上的動作提供者 `IFileContextActionProvider.GetActionsAsync`
  - 傳回`IFileContextAction`符合指定`FileContext.ContextType`值
- 檔案內容動作
  - 實作`IFileContextAction`和 <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` 屬性會傳回 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` 已`0x1000`組建，`0x1010`重建，或`0x1020`的清除

>[!NOTE]
>因為`FileDataValue`必須要編製索引，會有一段時間之間開啟的工作區和在掃描檔案的完整建置功能的點。 延遲會顯示在第一次開啟資料夾的因為沒有任何先前快取的索引。

## <a name="reporting-messages-from-a-build"></a>從組建報告訊息

建置可以資訊、 警告和錯誤訊息，向使用者呈現兩種方式之一。 簡單的方式是使用<xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService>，並提供<xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>，就像這樣：

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

`BuildMessage.Type` 和`BuildMessage.LogMessage`控制行為的資訊呈現給使用者的位置。 任何`BuildMessage.TaskType`以外的其他值`None`會產生**錯誤清單**項目，以指定的詳細資訊。 `LogMessage` 一律會在輸出**建置**窗格**輸出**工具視窗。

或者，延伸模組可以直接互動**錯誤清單**或是**建置**窗格。 在 Visual Studio 2017 版本 15.7 之前的版本有 bug 所在`pszProjectUniqueName`引數<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*>會被忽略。

>[!WARNING]
>呼叫端`IFileContextAction.ExecuteAsync`可以提供任意的基礎實作`IProgress<IFileContextActionProgressUpdate>`引數。 永遠不會叫用`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`直接。 目前沒有任何一般的指導方針，使用這個引數，但這些指導方針可能會有所變更。

## <a name="build-related-apis"></a>組建相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 提供建置組態詳細資料。
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 顯示<xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>的使用者。

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json 和 launch.vs.jason

如需撰寫 tasks.vs.json 或 launch.vs.json 檔案資訊，請參閱[自訂建置與偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)。

## <a name="next-steps"></a>後續步驟

* [語言伺服器通訊協定](language-server-protocol.md)-了解如何整合到 Visual Studio 語言伺服器。