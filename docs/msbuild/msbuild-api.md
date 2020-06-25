---
title: MSBuild API | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9d3cdaf2bcc7d7c62f7224c3a8c439d03282ef0
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371920"
---
# <a name="use-the-msbuild-api"></a>使用 MSBuild API

MSBuild 提供公開的 API 介面，讓您的程式可以執行建置並檢查專案。 您可以在下列 NuGet 套件中找到最新版本的 MSBuild Api：

| 套件名稱 | 描述 |
| ------------ | ----------- |
| [Microsoft.Build](https://www.nuget.org/packages/Microsoft.Build) | 包含用來建立、編輯和評估 MSBuild 專案的 Microsoft Build 元件。|
| [Microsoft.Build.Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| 包含其他 MSBuild 元件所使用的一般 MSBuild framework 元件。 |
| [Microsoft Build。執行時間](https://www.nuget.org/packages/Microsoft.Build.Runtime) | 傳遞 MSBuild 的完整可執行檔複本。 只有當您的應用程式需要載入專案或執行同進程組建，而不需要安裝 MSBuild 時，才參考此封裝。 使用此封裝成功評估專案需要將其他元件（例如編譯器）匯總至應用程式目錄。 |
| [Microsoft Build。 Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | 包含可實作為 MSBuild 常用工作的「內部工作」元件。 |
| [建立公用程式核心](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | 包含用來執行自訂 MSBuild 工作的 Microsoft. Build. 公用程式元件。 |

此外，NuGet 也會裝載舊版的元件，也就是已被取代的[組建引擎](https://www.nuget.org/packages/Microsoft.Build.Engine)。

MSBuild API 有數個不同的版本，而在15和16版中，NuGet 套件中有兩種不同形式的元件，一個是以 .NET Framework 編譯，另一個則使用 .NET Core 編譯，這是 .NET Framework API 介面的子集。  當您叫用 `dotnet` 命令時，以及在 Mac 和 Linux 系統上使用 msbuild 時，會使用 msbuild 的 .Net Core 版本。

您可以使用[.NET API 瀏覽器](/dotnet/api)或流覽下列清單中的命名空間，找到 MSBuild API 的檔。

::: moniker range="vs-2017"
| 命名空間 | 套用至 | 描述 |
|-----------| -----------| ----------- |
| [Microsoft. Build. 建設](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15) | 全部 |  包含型別，由 MSBuild 物件模型搭配未評估的值用來建構專案根目錄。 每個專案根目錄對應至專案或目標檔案。 |
| [建立定義](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15) | 全部 | 包含 `ProjectOptions` 支援專案結構的類別。 |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15) | 全部 | 包含 MSBuild 物件模型用來評估專案的型別。 每個專案與一個或多個專案根目錄相關聯。 |
| [建立的內容](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15) | 全部 | 包含 `EvaluationContext` 類別，用來跨呼叫儲存評估狀態。 |
| [建立例外狀況](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15) | 全部 | 包含可能在建置流程期間擲回的例外狀況型別。 |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15) | 全部 | 包含由 MSBuild 物件模型用來建置專案的型別。 |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15) | 全部 | 包含定義工作和記錄器如何與 MSBuild 引擎互動的類型。|
| [建立 Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15) | 全部 | 包含支援效能分析的類型。 |
| [XamlTypes。](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15) | 僅 .NET Framework | 包含用來表示從檔案、規則和其他來源剖析之 XAML 類型的類別。 |
| [Microsoft. 建立萬用字元](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15) | 全部 | 包含支援萬用字元處理的類別。 |
| [Microsoft. 建立副檔名。](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15) | 全部 | 包含支援萬用字元處理擴充功能的類型。 |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15) | 全部 | 包含支援 `-graph` MSBuild 參數的類型。 |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15) | 全部 | 包含用於記錄組建之進度的型別。 |
| [ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15) | 全部 | 包含在 MSBuild 中支援遠端功能的類型。 |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15) | 全部 | 包含 MSBuild 所傳送之所有工作的執行。 |
| [建立部署程式。](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15) | 僅 .NET Framework | 包含 MSBuild 在內部使用的類別。 |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15) | 僅 .NET Framework | 包含 MSBuild 所使用的類別。|
| [Microsoft Build。裝載](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15) | 全部 | 包含 MSBuild 在內部使用的類別。 |
| [建立 Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15) | 僅 .NET Framework | 包含與 XAML 組建工作相關的類別。 |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15) | 全部 | 包含 helper 類別，您可以用來建立自己的 MSBuild 記錄器和工作。|
:::moniker-end
:::moniker range=">=vs-2019"
| 命名空間 | 套用至 | 描述 |
|-----------| -----------| ----------- |
| [Microsoft. Build. 建設](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16) | 全部 |  包含型別，由 MSBuild 物件模型搭配未評估的值用來建構專案根目錄。 每個專案根目錄對應至專案或目標檔案。 |
| [建立定義](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16) | 全部 | 包含 `ProjectOptions` 支援專案結構的類別。 |
| [Microsoft.Build.Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16) | 全部 | 包含 MSBuild 物件模型用來評估專案的型別。 每個專案與一個或多個專案根目錄相關聯。 |
| [建立的內容](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16) | 全部 | 包含 `EvaluationContext` 類別，用來跨呼叫儲存評估狀態。 |
| [建立例外狀況](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16) | 全部 | 包含可能在建置流程期間擲回的例外狀況型別。 |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16) | 全部 | 包含由 MSBuild 物件模型用來建置專案的型別。 |
| [Microsoft.Build.Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16) | 全部 | 包含定義工作和記錄器如何與 MSBuild 引擎互動的類型。|
| [建立 Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16) | 全部 | 包含支援效能分析的類型。 |
| [XamlTypes。](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16) | 僅 .NET Framework | 包含用來表示從檔案、規則和其他來源剖析之 XAML 類型的類別。 |
| [Microsoft. 建立萬用字元](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16) | 全部 | 包含支援萬用字元處理的類別。 |
| [Microsoft. 建立副檔名。](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16) | 全部 | 包含支援萬用字元處理擴充功能的類型。 |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16) | 全部 | 包含支援 `-graph` MSBuild 參數的類型。 |
| [Microsoft.Build.Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16) | 全部 | 包含用於記錄組建之進度的型別。 |
| [ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16) | 全部 | 包含在 MSBuild 中支援遠端功能的類型。 |
| [Microsoft.Build.Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16) | 全部 | 包含 MSBuild 所傳送之所有工作的執行。 |
| [建立部署程式。](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16) | 僅 .NET Framework | 包含 MSBuild 在內部使用的類別。 |
| [Microsoft.Build.Tasks.Deployment.ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16) | 僅 .NET Framework | 包含 MSBuild 所使用的類別。|
| [Microsoft Build。裝載](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16) | 全部 | 包含 MSBuild 在內部使用的類別。 |
| [建立 Xaml](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16) | 僅 .NET Framework | 包含與 XAML 組建工作相關的類別。 |
| [Microsoft.Build.Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16) | 全部 | 包含 helper 類別，您可以用來建立自己的 MSBuild 記錄器和工作。|
:::moniker-end

在上表中，[適用于] 資料行中的所有都表示命名空間中的類型可用於 .NET Framework 和 .NET Core 版本的 MSBuild API。
