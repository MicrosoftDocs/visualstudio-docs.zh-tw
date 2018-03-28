---
title: 在 Visual Studio 工作區中建置 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 258a64794712da92b881f3798255efc60cfdbe5c
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="workspace-build"></a>工作區中的組建

建置支援[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)案例需要提供的擴充項[編製索引](workspace-indexing.md)和[檔案內容](workspace-file-contexts.md)資料[工作區](workspaces.md)，做為以及要執行的建置動作。

以下是您的擴充功能將需要的外框。

## <a name="build-file-context"></a>建立檔案的內容

- 提供者處理站
  - `ExportFileContextProviderAttribute` 屬性附帶`supportedContextTypeGuids`為所有適用`string`常數 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextProvider>`
  - 檔案內容提供者
    - 傳回`FileContext`每個建置作業和支援的組態
      - `contextType` 從 <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` 實作<xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext>與`Configuration`屬性做為組建組態 (例如`"Debug|x86"`， `"ret"`，或`null`若不適用)。 或者，使用的執行個體<xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>。 組態值**必須**比對索引的檔案資料值的組態。

## <a name="indexed-build-file-data-value"></a>索引的組建檔案資料值

- 提供者處理站
  - `ExportFileScannerAttribute` 屬性附帶`IReadOnlyCollection<FileDataValue>`為支援的類型
  - 實作 `IWorkspaceProviderFactory<IFileScanner>`
- 上的檔案掃描 `ScanContentAsync<T>`
  - 傳回資料時`FileScannerTypeConstants.FileDataValuesType`是型別引數
  - 傳回針對每個組態，以建構檔案資料值：
    - `type` 做為 `BuildConfigurationContext.ContextTypeGuid`
    - `context` 為您的組建組態 (例如`"Debug|x86"`， `"ret"`，或`null`若不適用)。 此值**必須**符合從檔案內容的組態。

## <a name="build-file-context-action"></a>建置的檔案內容的動作

- 提供者處理站
  - `ExportFileContextActionProvider` 屬性附帶`supportedContextTypeGuids`為所有適用`string`常數 `BuildContextTypes`
  - 實作 `IWorkspaceProviderFactory<IFileContextActionProvider>`
- 上的動作提供者 `IFileContextActionProvider.GetActionsAsync`
  - 傳回`IFileContextAction`符合給定`FileContext.ContextType`值
- 檔案內容的動作
  - 實作`IFileContextAction`和 <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` 屬性會傳回 `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` 是`0x1000`建置，`0x1010`重建，或`0x1020`的初始狀態

>[!NOTE]
>因為`FileDataValue`要編製索引，需要將某些開啟的工作區，然後在掃描檔案的完整建置功能的點之間的時間量。 延遲將會看到第一個開啟的資料夾，所以沒有先前的快取的索引。

## <a name="reporting-messages-from-a-build"></a>從組建報告訊息

組建就會出現資訊、 警告和錯誤訊息給使用者有兩種。 簡單的方式是使用<xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService>並提供<xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>，就像這樣：

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

`BuildMessage.Type` 和`BuildMessage.LogMessage`控制行為的資訊呈現給使用者的位置。 任何`BuildMessage.TaskType`以外值`None`會產生**錯誤清單**項目具有指定詳細資料。 `LogMessage` 一律會在輸出**建置**窗格**輸出**工具視窗。

或者，延伸模組可以直接互動**錯誤清單**或**建置**窗格。 在 Visual Studio 2017 版本 15.7 之前的版本有 bug 其中`pszProjectUniqueName`引數的<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*>會被忽略。

>[!WARNING]
>呼叫端的`IFileContextAction.ExecuteAsync`可以提供任意的基礎實作`IProgress<IFileContextActionProgressUpdate>`引數。 永遠不會叫用`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`直接。 目前沒有一般的指導方針使用這個引數，但這些方針有可能變更。

## <a name="build-related-apis"></a>組建相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> 提供建置組態的詳細資料。
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> 顯示<xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>的使用者。

## <a name="tasksvsjson-and-launchvsjson"></a>tasks.vs.json 和 launch.vs.json

如需撰寫 tasks.vs.json 或 launch.vs.json 檔案資訊，請參閱[自訂建置和偵錯工作](../ide/customize-build-and-debug-tasks-in-visual-studio.md)。

## <a name="next-steps"></a>後續步驟

* [語言伺服器通訊協定](language-server-protocol.md)-了解如何將伺服器語言整合到 Visual Studio。