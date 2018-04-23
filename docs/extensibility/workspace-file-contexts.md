---
title: 在 Visual Studio 中的工作區的檔案內容 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="workspace-file-contexts"></a>工作區中檔案的內容

所有的深入剖析[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區所產生的 「 檔案內容提供者 > 可實作<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider>介面。 這些擴充功能可能會尋找資料夾中的模式或檔案，讀取 MSBuild 檔和 makefile，偵測等封裝相依性才能累積它們需要定義的檔案內容的深入資訊。 單獨使用時的檔案內容不會執行任何動作，而是提供另一個延伸模組接著可以處理的資料。

每個<xref:Microsoft.VisualStudio.Workspace.FileContext>具有`Guid`與其相關聯識別的資料類型，它執行。 工作區會使用此`Guid`更新版本，才能符合具有延伸模組可使用透過資料<xref:Microsoft.VisualStudio.Workspace.FileContext.Context>屬性。 識別哪些檔案內容的中繼資料與匯出檔案的內容提供者`Guid`s 它可能會產生資料。

定義之後，可以是任意數目的工作區中檔案或資料夾相關聯的檔案內容。 指定的檔案或資料夾可能是相關聯的檔案內容的任何數目。 它是多對多關聯性。

建置、 偵錯，並語言服務相關之檔案的內容最常見的案例。 如需詳細資訊，請參閱與這些案例相關的其他主題。

## <a name="file-context-lifecycle"></a>檔案內容的生命週期

週期，可供`FileContext`是不具決定性。 在任何時間，元件可以以非同步方式要求內容類型的某些設定。 將查詢提供者支援某個子集的要求內容類型。 `IWorkspace`執行個體則當做 man 消費者和提供者透過之間<xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A>方法。 取用者可能會要求內容，而且執行內容為基礎，而其他人可能會要求內容，以及維護長期的參考某些短期的動作。 

變更可能會導致變成過期的檔案內容的檔案，就可能發生。 提供者可以在引發事件`FileContext`通知取用者的更新。 比方說，如果建置內容會提供一些檔案，但是未在磁碟上的變更會使該內容，然後原始生產者可以叫用此事件。 仍然參考的任何取用者`FileContext`然後可以對新 requery `FileContext`。

>[!NOTE]
>沒有取用者發送模型。 取用者將不會收到通知的提供者的新`FileContext`之後其要求。

## <a name="expensive-file-context-computations"></a>檔案的昂貴費用內容計算

尤其是提供者必須解決檔案之間的關聯性，可以是高度耗費資源，從磁碟讀取檔案內容。 比方說，有些來源檔案的檔案內容中，查詢提供者，但檔案內容是從專案檔案的中繼資料而定。 剖析專案檔，或評估使用 MSBuild 是高度耗費資源。 相反地，擴充功能可以匯出`IFileScanner`建立`FileDataValue`工作區建立索引期間的資料。 現在當系統要求您的檔案內容`IFileContextProvider`可快速地查詢該索引的資料。 如需有關索引的詳細資訊，請參閱[編製索引的工作區](workspace-indexing.md)主題。

>[!WARNING]
>其他方法，請務必謹慎您`FileContext`可能高度耗費資源，來計算。 某些 UI 互動會同步，而且依賴大量`FileContext`要求。 範例包括開啟編輯器索引標籤並開啟**方案總管 中**操作功能表。 這些動作會使輸入要求的許多建置內容。

## <a name="file-context-related-apis"></a>檔案內容相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> 保存資料和中繼資料。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 和<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1>建立的檔案內容。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> 將匯出檔案的內容提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 是取用者用來取得檔案內容。
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 定義組建會耗用開啟資料夾的內容類型。

## <a name="file-context-actions"></a>檔案內容的動作

雖然`FileContext`本身是有關某些檔，只是資料<xref:Microsoft.VisualStudio.Workspace.IFileContextAction>是 express，並在該資料上執行的方法。 `IFileContextAction` 是在其使用方式的彈性。 兩個最常見的情況下會建置和偵錯。

## <a name="reporting-progress"></a>報告進度

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>方法傳遞`IProgress<IFileContextActionProgressUpdate>`，但不應使用引數為該型別。 `IFileContextActionProgressUpdate` 是空的介面，並叫用`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`可能會擲回`NotImplementedException`。 相反地，`IFileContextAction`必須轉換成視案例的另一個類型引數。

如需 Visual Studio 所提供的類型資訊，請參閱個別案例的文件。

## <a name="file-context-action-related-apis"></a>檔案內容動作相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 執行基礎的某些行為`FileContext`。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> 建立的執行個體`IFileContextAction`。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 匯出型別`IWorkspaceProviderFactory<IFileContextActionProvider>`。

## <a name="file-watching"></a>檔案監視

工作區會接聽檔案變更告知，並提供<xref:Microsoft.VisualStudio.Workspace.IFileWatcherService>透過<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>。 比對"ExcludedItems 」 設定的檔案不會產生檔案通知事件。 事件之間的臨界值用於通知簡化和重複減少。 當您需要做出回應檔案有所變更時，您必須訂閱此服務。

>[!TIP]
>工作區[索引服務](workspace-indexing.md)預設訂閱檔案的事件。 檔案加入和修改會導致相關`IFileScanner`的事件要叫用為新的資料，該檔案。 檔案刪除將會移除索引的資料。 您不需要訂閱您`IFileScanner`檔案監看員服務。

## <a name="next-steps"></a>後續步驟

* [索引](workspace-indexing.md)-編製索引的工作區會收集並保存的工作區的相關資訊。
* [工作區](workspaces.md)-檢閱工作區的概念和設定儲存體。
