---
title: Visual Studio 中的工作區索引 |Microsoft Docs
description: 深入瞭解工作區編制索引，這是資料的集合和持續性儲存，可針對開啟的資料夾工作區支援豐富的 IDE 功能。
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877048"
---
# <a name="workspace-indexing"></a>工作區索引

在解決方案中，專案系統負責提供組建、偵錯工具、 **GoTo** 符號搜尋等功能。 專案系統可以執行這項工作，因為他們瞭解專案內檔案的關聯性和功能。 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區需要相同的深入解析，才能提供豐富的 IDE 功能。 這項資料的收集和持續性儲存體是稱為工作區索引的進程。 此索引資料可透過一組非同步 Api 查詢。 擴充項可以藉由提供 <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> 知道如何處理特定檔案類型的來參與編制索引程式。

## <a name="types-of-indexed-data"></a>索引資料的類型

有三種資料已編制索引。 請注意，file 掃描器預期的類型與從索引還原序列化的類型不同。

|資料|檔案掃描器類型|索引查詢結果類型|相關類型|
|--|--|--|--|
|參考資料|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|符號|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 應該用來取代 `IIndexWorkspaceService` 查詢|
|資料值|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>查詢索引資料

有兩種非同步類型可用來存取保存的資料。 第一個是透過 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> 。 它提供單一檔案和資料的基本存取 `FileReferenceResult` 權 `FileDataResult` ，並快取結果。 第二個是 <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> ，它不會使用快取，但可提供更多的查詢功能。

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>參與編制索引

工作區索引大致會遵循下列順序：

1. 在工作區中探索和保存檔案系統實體只 (初始開啟掃描) 。
1. 針對每個檔案，系統會要求具有最高優先順序的相符提供者進行掃描 `FileReferenceInfo` 。
1. 針對每個檔案，系統會要求具有最高優先順序的相符提供者進行掃描 `SymbolDefinition` 。
1. 每個檔案都會要求所有提供者 `FileDataValue` 。

擴充功能可以藉由使用來執行和匯出型別來匯出掃描器 `IWorkspaceProviderFactory<IFileScanner>` <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> 。 `SupportedTypes`屬性引數應該是中的一或多個值 <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> 。 如需範例掃描器，請參閱 VS SDK [範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)。

> [!WARNING]
> 請勿匯出支援類型的檔掃描器 `FileScannerTypeConstants.FileScannerContentType` 。 它僅供 Microsoft 內部用途使用。

在 advanced 的情況下，延伸模組可能會動態支援任意一組檔案類型。 擴充功能可以匯出，而不是 MEF 匯出 `IWorkspaceProviderFactory<IFileScanner>` `IWorkspaceProviderFactory<IFileScannerProvider>` 。 開始編制索引時，會匯入並具現化此 factory 類型，並叫用其 <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> 方法。 `IFileScanner` 將會接受支援任何值的實例 `FileScannerTpeConstants` ，而不只是符號。

## <a name="next-steps"></a>後續步驟

* [工作區和語言服務](workspace-language-services.md) -瞭解如何將語言服務整合至開啟的資料夾工作區。
* [工作區組建](workspace-build.md) -開啟資料夾支援 MSBuild 和 makefile 等組建系統。