---
title: MSBuild 保留和已知屬性 | Microsoft Docs
description: 瞭解 MSBuild 保留和已知屬性、預先定義的屬性，這些屬性會儲存專案檔和 MSBuild 二進位檔的相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384924"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild 保留和已知屬性

MSBuild 提供一組預先定義的屬性，用來儲存專案檔和 MSBuild 二進位檔的相關資訊。 這些屬性的評估方式與其他 MSBuild 屬性相同。 例如，若要使用 `MSBuildProjectFile` 屬性，請輸入 `$(MSBuildProjectFile)`。

 MSBuild 會使用下表中的值預先定義保留和已知的屬性。 保留的屬性不能覆寫，但是已知的屬性可以使用同名的環境屬性、全域屬性或專案檔中宣告的屬性加以覆寫。

## <a name="reserved-and-well-known-properties"></a>保留和已知屬性

本節中的表格顯示 MSBuild 預先定義屬性。 資料表中的範例資料行會與下列範例專案檔相關，並在專案檔中使用 `C:\Source\Repos\ConsoleApp1\ConsoleApp1` 時，顯示這些屬性的值，在專案檔中存取 MSBuild 時，沒有特殊命令列選項，且已安裝 Visual Studio 2019 16.7 版的預覽組建。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| 屬性 | 保留或已知 | 描述 | 範例 |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | 保留 | 目前正在使用之 MSBuild 二進位檔所在資料夾的絕對路徑 (例如 *C:\Windows\Microsoft.Net\Framework \\ \<versionNumber>*) 。 如果您必須參考 MSBuild 目錄中的檔案，這個屬性就很有用。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | 已知 | 於 .NET Framework 4 中引入：`MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32` 兩者的預設值並無差異。 您可以將環境變數 `MSBUILDLEGACYEXTENSIONSPATH` 設定為非 null 值，藉此啟用舊版中 `MSBuildExtensionsPath` 之預設值的行為。<br /><br /> 在 .NET Framework 3.5 (含) 以前版本中，`MSBuildExtensionsPath` 的預設值會指向 *\Program Files\\* 或 *\Program Files (x86)* 資料夾下 MSBuild 子資料夾的路徑 (根據目前處理序的位元而定)。 例如，若是 64 位元電腦上的 32 位元處理序，這個屬性會指向 *\Program Files (x86)* 資料夾。 若是 64 位元電腦上的 64 位元處理序，這個屬性會指向 *\Program Files* 資料夾。<br /><br /> 不要在這個屬性中包含結尾的反斜線。<br /><br /> 這個位置是放置目標檔案的理想位置。 例如，您的目標檔案可以安裝於 *\Program Files\MSBuild\MyFiles\Northwind.targets*，然後使用下面這個 XML 程式碼匯入專案檔中：<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | 已知 | *\Program* 檔案或 \Program 檔下的 MSBuild 子資料夾路徑 *(x86)* 資料夾。 路徑一律指向 32 位元電腦上的 32 位元 *\Program Files (x86)* 資料夾，以及 64 位元電腦上的 *\Program Files*。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath64`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | 已知 | *\Program Files* 資料夾下 MSBuild 子資料夾的路徑。 若是 64 位元電腦，這個路徑永遠指向 *\Program Files* 資料夾。 若是 32 位元電腦，這個路徑是空白的。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | 保留 | `true` 如果 MSBuild 以互動方式執行，則允許使用者輸入。 這項設定是由 `-interactive` 命令列選項所控制。 | `false` |
| `MSBuildLastTaskResult` | 保留 | 如果前述工作順利完成且沒有任何錯誤 (即使有警告)，則為 `true`，如果前述工作發生錯誤，則為 `false`。 通常在工作中發生錯誤時，錯誤會在該專案中最後發生。 因此，這個屬性的值絕不會是 `false`，但下列情節除外：<br /><br /> - 將 [Task 項目 (MSBuild)](../msbuild/task-element-msbuild.md) 的 `ContinueOnError` 屬性設為 `WarnAndContinue` (或 `true`) 或 `ErrorAndContinue` 時。<br /><br /> - 當 `Target` 具有 [OnError 項目 (MSBuild)](../msbuild/onerror-element-msbuild.md) 作為子項目時。 | `true` |
| `MSBuildNodeCount` | 保留 | 建置時使用的並行處理序數目上限。 這是您在命令列中為 **-maxcpucount** 指定的值。 如果您已指定 **-maxcpucount**，但未指定值，則 `MSBuildNodeCount` 會指定電腦中的處理器數目。 如需詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)和[平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。 | 1 |
| `MSBuildProgramFiles32` | 保留 | 32 位元程式資料夾的位置，例如 *C:\Program Files (x86)*。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | 保留 | `DefaultTargets` 項目的 `Project` 屬性中所指定目標的完整清單。 例如，下列 `Project` 項目的 `MSBuildDefaultTargets` 屬性值為 `A;B;C`。<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | 保留 | 專案檔所在目錄的絕對路徑，例如 *C:\MyCompany\MyProduct*。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | 保留 | `MSBuildProjectDirectory` 屬性的值，不包含根磁碟機。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | 保留 | 專案檔的副檔名，包括句點;例如， *proj*。 | `.csproj`|
| `MSBuildProjectFile` | 保留 | 專案檔的完整檔名，包括副檔名，例如 *MyApp.proj*。 | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | 保留 | 專案檔的絕對路徑和完整檔名，包括副檔名，例如 *C:\MyCompany\MyProduct\MyApp.proj*。 | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | 保留 | 專案檔的檔案名稱，不包括副檔名，例如 *MyApp*。 | `ConsoleApp1` |
| `MSBuildRuntimeType` | 保留 | 目前執行的執行階段類型。 已在 MSBuild 15 中引入。 在 MSBuild 15) 之前，值可能是未定義 `Full` 的 (，表示 msbuild 是在桌面 .NET Framework 上 `Core` 執行，指出 msbuild 是在 .net Core 上執行 (例如在) 中執行 `dotnet build` ，或是 `Mono` 表示 msbuild 正在 Mono 上執行。 | `Full` |
| `MSBuildStartupDirectory` | 保留 | 呼叫 MSBuild 之資料夾的絕對路徑。 藉由使用這個屬性，您可以在專案樹狀結構中的特定點底下建立所有專案，而不需要在每個目錄 *\<dirs> 中建立專案檔。* 而您只會有一個專案，例如 *c:\traversal.proj*，如下所示：<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> 若要在樹狀結構中的任何點進行建置，請輸入：<br /><br /> `msbuild c:\traversal.proj`<br /><br /> 不要在這個屬性中包含結尾的反斜線。 | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | 保留 | `MSBuildThisFileFullPath` 的檔案名稱和副檔名部分。 | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | 保留 | `MSBuildThisFileFullPath` 的目錄部分。<br /><br /> 在路徑中包含結尾的反斜線。 | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | 保留 | `MSBuildThisFileFullPath` 的目錄部分，不包括根磁碟機。<br /><br /> 在路徑中包含結尾的反斜線。 | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | 保留 | `MSBuildThisFileFullPath` 的副檔名部分。 | `.csproj` |
| `MSBuildThisFileFullPath` | 保留 | 包含執行中目標之專案檔或 targets 檔的絕對路徑。<br /><br /> 提示：您可以在目標檔案中指定相對於目標檔 (而不是相對於原始專案檔) 的相對路徑。 | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | 保留 | `MSBuildThisFileFullPath` 的檔案名稱部分，不包含副檔名。 | `ConsoleApp1` |
| `MSBuildToolsPath` | 保留 | 與值相關聯之 MSBuild 版本的安裝路徑 `MSBuildToolsVersion` 。<br /><br /> 不要在路徑中包含結尾的反斜線。<br /><br /> 這個屬性無法覆寫。 | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | 保留 | 用來建立專案的 MSBuild 工具組版本。<br /><br /> 注意： MSBuild 工具組包含用來建立應用程式的工作、目標和工具。 工具包括編譯器，例如 *csc.exe* 和 vbc.exe。 如需詳細資訊，請參閱 [工具組 (ToolsVersion) ](../msbuild/msbuild-toolset-toolsversion.md)以及 [標準和自訂工具](../msbuild/standard-and-custom-toolset-configurations.md)組設定。 | `Current` |
| `MSBuildVersion` | 保留 | 用來建立專案的 MSBuild 版本。 <br /><br/> 這個屬性無法覆寫，否則就會傳回錯誤訊息 `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`。 | 16.11.0 |
| `MSBuildAssemblyVersion` | 保留 | 用來建立專案的 MSBuild 元件版本。 | 16.0 |
| `MSBuildFileVersion` | 保留 | 用來建立專案的 MSBuild 元件的4部分版本。 | 16.11.0.30701 |
| `MSBuildSemanticVersion` | 保留 | 用來建立專案之 MSBuild 元件的完整 semver 2.0 版本。 | 16.11.0-preview-21302-05 + 5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>與 MSBuild 項目發生衝突的名稱

除了上述項目，對應至 MSBuild 語言項目的名稱也無法用於使用者定義的屬性、項目或項目中繼資料：

* VisualStudioProject
* 目標
* PropertyGroup
* 輸出
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Choose
* 當
* Otherwise

## <a name="see-also"></a>另請參閱

- [MSBuild 參考](../msbuild/msbuild-reference.md)

- [MSBuild 屬性](../msbuild/msbuild-properties.md)
