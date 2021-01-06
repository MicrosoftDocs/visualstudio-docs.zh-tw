---
title: Visual Studio 中的工作區檔案內容 |Microsoft Docs
description: 瞭解可執行 IFileCoNtextProvider 介面的檔案內容提供者，以支援對開啟資料夾工作區的見解。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 271b05d78123136d47cb618e8ed38cea64b7beac
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877061"
---
# <a name="workspace-file-contexts"></a>工作區檔案內容

[開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區的所有見解都是由執行介面的「檔案內容提供者」所產生 <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 。 這些延伸模組可能會尋找資料夾或檔案中的模式、讀取 MSBuild 檔案和 makefile、偵測套件相依性等等，以便累積定義檔案內容所需的見解。 檔案內容本身不會執行任何動作，而是會提供另一個擴充功能可處理的資料。

每個都 <xref:Microsoft.VisualStudio.Workspace.FileContext> 有與其 `Guid` 相關聯的，可識別它所攜帶的資料類型。 工作區 `Guid` 稍後會使用此屬性來比對透過屬性取用資料的延伸模組 <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> 。 檔案內容提供者會使用可識別可能產生資料之檔案內容的中繼資料匯出 `Guid` 。

一旦定義之後，檔案內容可以與工作區中的任何數目的檔案或資料夾相關聯。 指定的檔案或資料夾可能與任意數量的檔案內容相關聯。 這是多對多關聯性。

檔案內容的最常見案例是與組建、偵錯工具和語言服務相關。 如需詳細資訊，請參閱這些案例的其他相關主題。

## <a name="file-context-lifecycle"></a>檔案內容生命週期

的生命週期為 `FileContext` 不具決定性。 元件可在任何時間以非同步方式要求某一組內容類型。 將會查詢支援某些要求內容類型子集的提供者。 此 `IWorkspace` 實例可作為取用者與提供者之間透過方法的中間人 <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 。 取用者可能會要求內容，並根據內容執行一些短期動作，有些則可能會要求內容並維護長期的參考。

變更可能會導致檔案內容過期的檔案。 提供者可以在上引發事件 `FileContext` ，以通知取用者有更新。 例如，如果提供某個檔案的組建內容，但磁片上的變更使該內容失效，則原始生產者可以叫用該事件。 任何仍在參考的取用者，都 `FileContext` 可以重新查詢新的 `FileContext` 。

>[!NOTE]
>沒有任何推播模型可供取用者使用。 取用者在要求之後，將不會收到提供者新的通知 `FileContext` 。

## <a name="expensive-file-context-computations"></a>昂貴的檔案內容計算

從磁片讀取檔案內容可能會很耗費資源，尤其是當提供者需要解析檔案之間的關聯性時。 例如，提供者可能會針對某些原始程式檔的檔案內容進行查詢，但是檔案內容會相依于專案檔中的中繼資料。 使用 MSBuild 剖析專案檔或評估是很昂貴的。 相反地，擴充功能可以匯出， `IFileScanner` 以 `FileDataValue` 在工作空間編制索引期間建立資料。 現在當系統要求您提供檔案內容時， `IFileContextProvider` 可以快速查詢該索引的資料。 如需編制索引的詳細資訊，請參閱 [工作區索引編制](workspace-indexing.md) 主題。

>[!WARNING]
>請注意， `FileContext` 計算成本可能很高的其他方式。 某些 UI 互動是同步的，並且依賴大量的 `FileContext` 要求。 範例包括開啟 [編輯器] 索引標籤，以及開啟 **方案總管** 的內容功能表。 這些動作會產生許多組建內容類型要求。

## <a name="file-context-related-apis"></a>檔案內容相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.FileContext> 保存資料和中繼資料。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> 並 <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> 建立檔案內容。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> 匯出檔案內容提供者。
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> 可供取用者用來取得檔案內容。
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> 定義開啟資料夾將使用的組建內容類型。

## <a name="file-context-actions"></a>檔案內容動作

雖然 `FileContext` 本身只是某些檔案)  (的相關資料，但它 <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 是一種表達和處理該資料的方法。 `IFileContextAction` 在使用上有彈性。 其中兩個最常見的案例是建立和偵錯工具。

## <a name="reporting-progress"></a>報告進度

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>傳遞方法時 `IProgress<IFileContextActionProgressUpdate>` ，不應使用引數做為該類型。 `IFileContextActionProgressUpdate` 是空的介面，且叫用 `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` 可能會擲回 `NotImplementedException` 。 相反地， `IFileContextAction` 必須視情況需要將引數轉換成另一種類型。

如需 Visual Studio 所提供之類型的詳細資訊，請參閱個別案例的檔。

## <a name="file-context-action-related-apis"></a>檔案內容動作相關的 Api

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> 根據來執行某些行為 `FileContext` 。
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> 建立的實例 `IFileContextAction` 。
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> 匯出型別 `IWorkspaceProviderFactory<IFileContextActionProvider>` 。

## <a name="file-watching"></a>檔案監看

工作區會接聽檔案變更通知，並提供 <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> via <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> 。 符合 "ExcludedItems" 設定的檔案將不會產生檔案通知事件。 事件之間的閾值會用於通知簡化和減少重複。 當您需要回應檔案變更時，您應該訂閱此服務。

>[!TIP]
>依預設，工作區的 [索引服務](workspace-indexing.md) 會訂閱檔案事件。 檔案新增和修改將會針對該檔案的新資料，叫用相關的 `IFileScanner` s 事件。 檔案刪除將會移除已編制索引的資料。 您不需要訂閱檔案監看員 `IFileScanner` 服務。

## <a name="next-steps"></a>後續步驟

* [編制索引](workspace-indexing.md) -工作區索引會收集和保存工作區的相關資訊。
* [工作](workspaces.md) 區-審核工作區概念和設定儲存體。
