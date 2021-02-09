---
title: MSBuild API | Microsoft Docs
description: 瞭解 MSBuild 提供的公用 API 介面，讓您的程式可以執行組建和檢查項目。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b376f1cb1d6b473c0ea37bb33f6ae2b60789fa24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919309"
---
# <a name="use-the-msbuild-api"></a>使用 MSBuild API

MSBuild 提供公開的 API 介面，讓您的程式可以執行建置並檢查專案。 您可以在下列 NuGet 套件中找到最新版本的 MSBuild Api：

| 套件名稱 | Description |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | 包含用來建立、編輯和評估 MSBuild 專案的 Microsoft Build 元件。|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| 包含其他 MSBuild 元件所使用的常見 MSBuild 架構元件。 |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | 提供 MSBuild 的完整可執行檔複本。 只有當您的應用程式需要載入專案或執行同進程組建，而不需要安裝 MSBuild 時，才參考此封裝。 使用此封裝成功評估專案需要匯總額外的元件， (像是) 入應用程式目錄中的編譯器。 |
| [Microsoft. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | 包含實作為 MSBuild 常用工作的 Microsoft. Tasks 元件。 |
| [的. 核心](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | 包含用來執行自訂 MSBuild 工作的 Microsoft Build. 公用程式元件。 |

此外，NuGet 也會裝載舊版元件，也就是已淘汰的 [版本](https://www.nuget.org/packages/Microsoft.Build.Engine)。

MSBuild API 有數種不同的版本，而在15和16版中，NuGet 套件中的元件有兩種不同的形式，一個是以 .NET Framework 編譯，另一個則是使用 .NET Core 編譯，也就是 .NET Framework API 介面的子集。  當您叫 `dotnet` 用命令時，以及在 Mac 和 Linux 系統上使用 msbuild 時，會使用 msbuild 的 .Net Core 版本。

您可以使用 [.NET Api 瀏覽器](/dotnet/api)或流覽下列清單中的命名空間，找到 MSBuild API 的檔。

::: moniker range="vs-2017"
| 命名空間 | 套用至 | Description |
|-----------| -----------| ----------- |
| [Microsoft. 建造](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | 全部 |  包含型別，由 MSBuild 物件模型搭配未評估的值用來建構專案根目錄。 每個專案根目錄對應至專案或目標檔案。 |
| [建立定義](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | 全部 | 包含 `ProjectOptions` 支援專案結構的類別。 |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | 全部 | 包含 MSBuild 物件模型用來評估專案的型別。 每個專案與一個或多個專案根目錄相關聯。 |
| [Microsoft. Build. CoNtext](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | 全部 | 包含 `EvaluationContext` 用來跨呼叫儲存評估狀態的類別。 |
| [Microsoft. Build. 例外狀況](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | 全部 | 包含可能在建置流程期間擲回的例外狀況型別。 |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | 全部 | 包含由 MSBuild 物件模型用來建置專案的型別。 |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | 全部 | 包含定義工作和記錄器如何與 MSBuild 引擎互動的型別。|
| [建立 Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | 全部 | 包含支援效能分析的類型。 |
| [XamlTypes。](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | 僅 .NET Framework | 包含類別，這些類別用來表示從檔案、規則和其他來源剖析的 XAML 類型。 |
| [Microsoft。](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | 全部 | 包含支援萬用字元處理的類別。 |
| [建立副檔名](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | 全部 | 包含支援萬用字元處理延伸模組的類型。 |
| [[建立]](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | 全部 | 包含支援 `-graph` MSBuild 參數的類型。 |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | 全部 | 包含用於記錄組建之進度的型別。 |
| [ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | 全部 | 包含在 MSBuild 中支援遠端處理的類型。 |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | 全部 | 包含 MSBuild 中所提供的所有工作實作。 |
| [。啟動載入器](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | 僅 .NET Framework | 包含 MSBuild 內部使用的類別。 |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | 僅 .NET Framework | 包含 MSBuild 使用的類別。|
| [建立工作。裝載](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | 全部 | 包含 MSBuild 內部使用的類別。 |
| [，App.xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | 僅 .NET Framework | 包含與 XAML 組建工作相關的類別。 |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | 全部 | 包含 helper 類別，可讓您用來建立自己的 MSBuild 記錄器和工作。|
:::moniker-end
:::moniker range=">=vs-2019"
| 命名空間 | 套用至 | Description |
|-----------| -----------| ----------- |
| [Microsoft. 建造](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | 全部 |  包含型別，由 MSBuild 物件模型搭配未評估的值用來建構專案根目錄。 每個專案根目錄對應至專案或目標檔案。 |
| [建立定義](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | 全部 | 包含 `ProjectOptions` 支援專案結構的類別。 |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | 全部 | 包含 MSBuild 物件模型用來評估專案的型別。 每個專案與一個或多個專案根目錄相關聯。 |
| [Microsoft. Build. CoNtext](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | 全部 | 包含 `EvaluationContext` 用來跨呼叫儲存評估狀態的類別。 |
| [Microsoft. Build. 例外狀況](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | 全部 | 包含可能在建置流程期間擲回的例外狀況型別。 |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | 全部 | 包含由 MSBuild 物件模型用來建置專案的型別。 |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | 全部 | 包含定義工作和記錄器如何與 MSBuild 引擎互動的型別。|
| [建立 Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | 全部 | 包含支援效能分析的類型。 |
| [XamlTypes。](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | 僅 .NET Framework | 包含類別，這些類別用來表示從檔案、規則和其他來源剖析的 XAML 類型。 |
| [Microsoft。](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | 全部 | 包含支援萬用字元處理的類別。 |
| [建立副檔名](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | 全部 | 包含支援萬用字元處理延伸模組的類型。 |
| [[建立]](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | 全部 | 包含支援 `-graph` MSBuild 參數的類型。 |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | 全部 | 包含用於記錄組建之進度的型別。 |
| [ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | 全部 | 包含在 MSBuild 中支援遠端處理的類型。 |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | 全部 | 包含 MSBuild 中所提供的所有工作實作。 |
| [。啟動載入器](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | 僅 .NET Framework | 包含 MSBuild 內部使用的類別。 |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | 僅 .NET Framework | 包含 MSBuild 使用的類別。|
| [建立工作。裝載](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | 全部 | 包含 MSBuild 內部使用的類別。 |
| [，App.xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | 僅 .NET Framework | 包含與 XAML 組建工作相關的類別。 |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | 全部 | 包含 helper 類別，可讓您用來建立自己的 MSBuild 記錄器和工作。|
:::moniker-end

在上表中，[套用到] 資料行中的全部，表示命名空間中的類型可用於 .NET Framework 和 .NET Core 版本的 MSBuild API。
