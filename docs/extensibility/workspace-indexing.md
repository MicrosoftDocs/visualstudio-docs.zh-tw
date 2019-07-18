---
title: 在 Visual Studio 中編製索引的工作區 |Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf7df777d27003fa5763debc772a8804ec28ef5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952692"
---
# <a name="workspace-indexing"></a>編製索引的工作區

在解決方案中，專案系統負責提供功能的建置、 偵錯**GoTo**符號搜尋，和更多功能。 專案系統可以進行這項工作，因為他們了解關聯性的專案中的檔案。 [開啟資料夾](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)工作區需要提供功能豐富的 IDE，以及相同的深入解析。 集合，此資料的永續性儲存體是稱為 工作區中編製索引的程序。 此索引的資料可透過一組非同步 Api 進行查詢。 擴充項可以參與索引的程序提供<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>，它知道如何處理某些類型的檔案。

## <a name="types-of-indexed-data"></a>索引的資料類型

有三種類型的資料編製索引。 請注意，從檔案掃描程式預期的類型不同於還原序列化從索引類型。

|資料|掃描器的檔案類型|索引查詢的結果類型|相關的類型|
|--|--|--|--|
|參考|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|符號|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> 應該使用而不是`IIndexWorkspaceService`查詢|
|資料值|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>查詢索引的資料

有兩個非同步類型可用來存取保存的資料。 第一個是透過<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>。 它提供單一檔案的基本存取權`FileReferenceResult`和`FileDataResult`資料，但會快取結果。 第二個是<xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService>不會使用快取，但可讓多個查詢的功能。

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

## <a name="participating-in-indexing"></a>參與編製索引

編製索引的工作區時，大約會遵循下列順序：

1. 探索及檔案系統中的實體 （僅限初始開啟掃描） 工作區的持續性。
1. 每個檔案，以最高優先順序相符的提供者會要求掃描`FileReferenceInfo`s。
1. 每個檔案，以最高優先順序相符的提供者會要求掃描`SymbolDefinition`s。
1. 每個檔案，所有提供者會要求輸入`FileDataValue`s。

擴充功能可以藉由實作匯出掃描器`IWorkspaceProviderFactory<IFileScanner>`匯出的類型和<xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>。 `SupportedTypes`屬性的引數應該是從一或多個值<xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>。 如範例的掃描器，請參閱 VS SDK[範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)。

> [!WARNING]
> 不會匯出檔案的掃描器支援`FileScannerTypeConstants.FileScannerContentType`型別。 它是 Microsoft 內部，僅供使用。

在進階情況下，擴充功能可能會以動態方式支援任意一組的檔案類型。 而不是 MEF 匯出`IWorkspaceProviderFactory<IFileScanner>`，延伸模組可以匯出`IWorkspaceProviderFactory<IFileScannerProvider>`。 編製索引開始時，此處理站型別會匯入，具現化，並具有其<xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A>叫用方法。 `IFileScanner` 支援的任何值的執行個體`FileScannerTpeConstants`將會被接受，不只是符號。

## <a name="next-steps"></a>後續步驟

* [工作區和語言服務](workspace-language-services.md)-了解如何整合的開啟資料夾 」 工作區中的語言服務。
* [工作區建置](workspace-build.md)-開啟資料夾支援建置系統，例如 MSBuild 和 makefile。