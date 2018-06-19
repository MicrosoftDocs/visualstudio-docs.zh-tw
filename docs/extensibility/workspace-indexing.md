---
title: 在 Visual Studio 中編製索引的工作區 |Microsoft 文件
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143422"
---
# <a name="workspace-indexing"></a>工作區的索引

在解決方案中，專案系統會負責提供功能建置、 偵錯**GoTo**搜尋符號，等等。 專案系統可以執行這項工作，因為他們了解的關聯性和專案內的檔案的功能。 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區需要提供功能豐富的 IDE，以及相同的深入資訊。 集合和永續性儲存體，這項資料是稱為 [索引] 工作區的處理序。 這個索引的資料可以透過一組非同步 Api 的查詢。 Extender 可以參與索引的程序提供<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>，它知道如何處理某些類型的檔案。

## <a name="types-of-indexed-data"></a>索引的資料類型

有三種類型的已編製索引的資料。 請注意檔案掃描器的預期的類型不同於還原序列化從索引類型。

|資料|檔案掃描器類型|索引查詢的結果型別|相關的類型|
|--|--|--|--|
|參考|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Symbol|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 應該使用而不是`IIndexWorkspaceService`查詢|
|資料值|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>查詢索引的資料

有兩個非同步類型可用來存取保存的資料。 第一個方法是透過<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>。 它提供單一檔案的基本存取`FileReferenceResult`和`FileDataResult`資料，以及其快取結果。 第二個是<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService>不使用快取，但允許多個查詢的功能。

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

## <a name="participating-in-indexing"></a>參與索引

工作區的索引大約會遵循下列順序：

1. 探索及檔案系統中的實體 （僅限在初始開啟掃描） 工作區的持續性。
1. 每個檔案，具有最高優先順序的比對提供者會掃描要求`FileReferenceInfo`s。
1. 每個檔案，具有最高優先順序的比對提供者會掃描要求`SymbolDefinition`s。
1. 每個檔案，所有的提供者會要求輸入`FileDataValue`s。

擴充功能可以藉由實作匯出掃描器`IWorkspaceProviderFactory<IFileScanner>`和匯出的類型與<xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>。 `SupportedTypes`屬性引數應該是從一或多個值<xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>。 如範例的掃描器，請參閱 VS SDK[範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)。

> [!WARNING]
> 不會匯出檔案掃描器支援`FileScannerTypeConstants.FileScannerContentType`型別。 用於 Microsoft 內部用途時，只有。

在進階的情況下，擴充功能可能會以動態方式支援任意一組的檔案類型。 而不是 MEF 匯出`IWorkspaceProviderFactory<IFileScanner>`，擴充功能可以匯出`IWorkspaceProviderFactory<IFileScannerProvider>`。 當索引開始時，此處理站型別會匯入，具現化，並有其<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A>叫用方法。 `IFileScanner` 支援的任何值的執行個體`FileScannerTpeConstants`將會接受，不只是符號。

## <a name="next-steps"></a>後續步驟

* [工作區和語言服務](workspace-language-services.md)-了解如何將語言服務整合到工作區中開啟資料夾。
* [工作區組建](workspace-build.md)-開啟資料夾支援建置 MSBuild 等 makefile 的系統。