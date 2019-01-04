---
title: 在 Visual Studio 中的工作區的檔案內容 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 93690eab989cee62d756a774675bf1d46da017fb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826860"
---
# <a name="workspace-file-contexts"></a>工作區的檔案內容

所有的深入了解[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區所產生的 「 檔案內容提供者 」 可實作<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider>介面。 這些擴充功能可能會尋找資料夾中的模式或檔案，讀取 MSBuild 檔和 makefile，偵測套件相依性等若要累積它們需要定義的檔案內容的深入解析。 檔案內容本身不會執行任何動作，，而是提供另一個延伸模組可以接著採取動作的資料。

每個<xref:Microsoft.VisualStudio.Workspace.FileContext>具有`Guid`與其相關聯識別的資料類型，它會執行。 工作區會使用這`Guid`更新版本，才能符合具有延伸模組可使用透過資料<xref:Microsoft.VisualStudio.Workspace.FileContext.Context>屬性。 檔案內容提供者以識別哪些檔案內容的中繼資料匯出`Guid`s 它可能會產生資料。

定義好之後，檔案內容可以是任意數目的檔案或資料夾中的工作區相關聯。 指定的檔案或資料夾可能是任何數目的檔案內容與相關聯。 它是多對多關聯性。

建立、 偵錯，以及語言服務相關的檔案內容最常見的案例。 如需詳細資訊，請參閱這些案例與相關的其他主題。

## <a name="file-context-lifecycle"></a>檔案內容生命週期

週期，可供`FileContext`是不具決定性。 在任何時間，元件可以以非同步方式要求內容類型的某些設定。 將查詢提供者支援的要求內容類型子集。 `IWorkspace`執行個體做為消費者和提供者之間的中間人<xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A>方法。 取用者可能會要求內容，並執行一些短期的動作，內容為基礎，而其他人可能會要求內容，以及維護的長時間執行的參考。 

變更可能會導致變成過期的檔案內容的檔案。 提供者可以在引發事件`FileContext`來通知取用者的更新。 例如，如果組建內容提供的一些檔案，但未在磁碟上的變更會導致無效的內容，然後原始的產生者可以叫用事件。 仍然參考之任何取用者`FileContext`然後可以對新 requery `FileContext`。

>[!NOTE]
>沒有取用者發送模型。 取用者不會收到通知的提供者的新`FileContext`之後其要求。

## <a name="expensive-file-context-computations"></a>檔案的昂貴費用的計算內容

提供者必須解決檔案之間的關聯性時，特別是，很高，從磁碟讀取檔案內容。 例如，某些原始程式檔的檔案內容，可以查詢提供者，但檔案內容是從專案檔的中繼資料而定。 剖析專案檔，或使用 MSBuild 評估它很昂貴。 相反地，擴充功能可以匯出`IFileScanner`來建立`FileDataValue`工作區中編製索引期間的資料。 現在當系統要求您的檔案內容`IFileContextProvider`可以快速地查詢該索引的資料。 如需有關如何編製索引的詳細資訊，請參閱 <<c0> [ 工作區索引編製](workspace-indexing.md)主題。

>[!WARNING]
>其他方法，請務必謹慎您`FileContext`可能很昂貴計算。 某些 UI 互動都是同步，並依賴大量`FileContext`要求。 範例包括開啟編輯器索引標籤，並開啟**方案總管 中**操作功能表。 這些動作，請輸入要求的許多建置內容。

## <a name="file-context-related-apis"></a>檔案內容相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> 保存資料和中繼資料。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 和<xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1>建立檔案的內容。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> 將匯出檔案的內容提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 會為取用者用來取得檔案內容。
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 定義建置會使用開啟資料夾的內容類型。

## <a name="file-context-actions"></a>檔案內容動作

雖然`FileContext`本身是關於某些檔案中，只是資料<xref:Microsoft.VisualStudio.Workspace.IFileContextAction>是 express，並依據該資料的方式。 `IFileContextAction` 很有彈性的使用量。 兩個最常見的案例是建置和偵錯。

## <a name="reporting-progress"></a>報告進度

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>方法會傳遞`IProgress<IFileContextActionProgressUpdate>`，但不應該使用引數為該型別。 `IFileContextActionProgressUpdate` 是空的介面，並叫用`IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)`可能會擲回`NotImplementedException`。 相反地，`IFileContextAction`必須轉換成另一個類型，視您的案例中的引數。

如需 Visual Studio 所提供的類型資訊，請參閱個別案例的文件。

## <a name="file-context-action-related-apis"></a>檔案內容動作相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 執行一些行為，根據`FileContext`。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> 建立的執行個體`IFileContextAction`。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 將匯出的型別`IWorkspaceProviderFactory<IFileContextActionProvider>`。

## <a name="file-watching"></a>檔案監看

工作區會接聽檔案變更通知，並提供<xref:Microsoft.VisualStudio.Workspace.IFileWatcherService>透過<xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>。 比對"ExcludedItems 」 設定的檔案不會產生檔案通知事件。 事件之間的臨界值使用於通知簡化，並減少重複。 當您需要做出檔案變更時，您應該訂閱此服務。

>[!TIP]
>工作區[編製索引服務](workspace-indexing.md)預設訂閱檔案的事件。 檔案新增與修改會導致相關`IFileScanner`的事件要叫用新的資料，該檔案。 檔案刪除將會移除索引的資料。 您不需要訂閱您`IFileScanner`檔案監看員服務。

## <a name="next-steps"></a>後續步驟

* [編製索引](workspace-indexing.md)-編製索引的工作區會收集並保存的工作區的相關資訊。
* [工作區](workspaces.md)-檢閱工作區的概念和儲存體設定。
