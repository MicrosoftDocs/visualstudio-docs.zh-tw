---
title: MSBuild 保留和已知屬性 | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35ef81aba75e42e7d3d713d5f6efb7129b55b2d2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632390"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild 保留和已知屬性
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 提供一組預先定義的屬性，用來儲存專案檔和 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 二進位檔的相關資訊。 這些屬性的評估方式與其他 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 屬性相同。 例如，若要使用 `MSBuildProjectFile` 屬性，請輸入 `$(MSBuildProjectFile)`。

 MSBuild 會使用下表中的值預先定義保留和已知的屬性。 保留的屬性不能覆寫，但是已知的屬性可以使用同名的環境屬性、全域屬性或專案檔中宣告的屬性加以覆寫。

## <a name="reserved-and-well-known-properties"></a>保留和已知屬性
 下表將描述 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 預先定義的屬性。


| 屬性 | 保留或已知 | 說明 |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | 保留 | 目前使用的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 二進位檔所在資料夾的絕對路徑 (例如 *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>*)。 如果您必須參考 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 目錄中的檔案，這個屬性會相當實用。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildExtensionsPath` | 已知 | 於 .NET Framework 4 中引入：`MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32` 兩者的預設值並無差異。 您可以將環境變數 `MSBUILDLEGACYEXTENSIONSPATH` 設定為非 null 值，藉此啟用舊版中 `MSBuildExtensionsPath` 之預設值的行為。<br /><br /> 在 .NET Framework 3.5 (含) 以前版本中，`MSBuildExtensionsPath` 的預設值會指向 *\Program Files\\* 或 *\Program Files (x86)* 資料夾下 MSBuild 子資料夾的路徑 (根據目前處理序的位元而定)。 例如，若是 64 位元電腦上的 32 位元處理序，這個屬性會指向 *\Program Files (x86)* 資料夾。 若是 64 位元電腦上的 64 位元處理序，這個屬性會指向 *\Program Files* 資料夾。<br /><br /> 不要在這個屬性中包含結尾的反斜線。<br /><br /> 這個位置是放置目標檔案的理想位置。 例如，您的目標檔案可以安裝於 *\Program Files\MSBuild\MyFiles\Northwind.targets*，然後使用下面這個 XML 程式碼匯入專案檔中：<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | 已知 | *\Program Files* 或 *\Program Files (x86)* 資料夾下 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 子資料夾的路徑。 路徑一律指向 32 位元電腦上的 32 位元 *\Program Files (x86)* 資料夾，以及 64 位元電腦上的 *\Program Files*。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath64`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildExtensionsPath64` | 已知 | *\Program Files* 資料夾下 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 子資料夾的路徑。 若是 64 位元電腦，這個路徑永遠指向 *\Program Files* 資料夾。 若是 32 位元電腦，這個路徑是空白的。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildLastTaskResult` | 保留 | 如果前述工作順利完成且沒有任何錯誤 (即使有警告)，則為 `true`，如果前述工作發生錯誤，則為 `false`。 通常在工作中發生錯誤時，錯誤會在該專案中最後發生。 因此，這個屬性的值絕不會是 `false`，但下列情節除外：<br /><br /> - 將 [Task 項目 (MSBuild)](../msbuild/task-element-msbuild.md) 的 `ContinueOnError` 屬性設為 `WarnAndContinue` (或 `true`) 或 `ErrorAndContinue` 時。<br /><br /> - 當 `Target` 具有 [OnError 項目 (MSBuild)](../msbuild/onerror-element-msbuild.md) 作為子項目時。 |
| `MSBuildNodeCount` | 保留 | 建置時使用的並行處理序數目上限。 這是您在命令列中為 **-maxcpucount** 指定的值。 如果您已指定 **-maxcpucount**，但未指定值，則 `MSBuildNodeCount` 會指定電腦中的處理器數目。 如需詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)和[平行建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。 |
| `MSBuildProgramFiles32` | 保留 | 32 位元程式資料夾的位置，例如 *C:\Program Files (x86)*。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildProjectDefaultTargets` | 保留 | `DefaultTargets` 項目的 `Project` 屬性中所指定目標的完整清單。 例如，下列 `Project` 項目的 `MSBuildDefaultTargets` 屬性值為 `A;B;C`。<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | 保留 | 專案檔所在目錄的絕對路徑，例如 *C:\MyCompany\MyProduct*。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildProjectDirectoryNoRoot` | 保留 | `MSBuildProjectDirectory` 屬性的值，不包含根磁碟機。<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildProjectExtension` | 保留 | 專案檔的副檔名，包括英文句號，例如 *.proj*。 |
| `MSBuildProjectFile` | 保留 | 專案檔的完整檔名，包括副檔名，例如 *MyApp.proj*。 |
| `MSBuildProjectFullPath` | 保留 | 專案檔的絕對路徑和完整檔名，包括副檔名，例如 *C:\MyCompany\MyProduct\MyApp.proj*。 |
| `MSBuildProjectName` | 保留 | 專案檔的檔案名稱，不包括副檔名，例如 *MyApp*。 |
| `MSBuildRuntimeType` | 保留 | 目前執行的執行階段類型。 已在 MSBuild 15 中引入。 在 MSBuild 15 之前可能未定義值，而 `Full` 指出 MSBuild 是在傳統型 .NET Framework 上執行、`Core` 指出 MSBuild 是在 .NET Core 上執行，或 `Mono` 指出 MSBuild 是在 Mono 上執行。 |
| `MSBuildStartupDirectory` | 保留 | 呼叫 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所在資料夾的絕對路徑。 使用這個屬性就可以在專案樹狀結構中建置特定點之下的所有項目，而不需要在每個目錄中建立 *\<dirs>.proj* 檔案。 而您只會有一個專案，例如 *c:\traversal.proj*，如下所示：<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> 若要在樹狀結構中的任何點進行建置，請輸入：<br /><br /> `msbuild c:\traversal.proj`<br /><br /> 不要在這個屬性中包含結尾的反斜線。 |
| `MSBuildThisFile` | 保留 | `MSBuildThisFileFullPath` 的檔案名稱和副檔名部分。 |
| `MSBuildThisFileDirectory` | 保留 | `MSBuildThisFileFullPath` 的目錄部分。<br /><br /> 在路徑中包含結尾的反斜線。 |
| `MSBuildThisFileDirectoryNoRoot` | 保留 | `MSBuildThisFileFullPath` 的目錄部分，不包括根磁碟機。<br /><br /> 在路徑中包含結尾的反斜線。 |
| `MSBuildThisFileExtension` | 保留 | `MSBuildThisFileFullPath` 的副檔名部分。 |
| `MSBuildThisFileFullPath` | 保留 | 包含執行中目標之專案檔或 targets 檔的絕對路徑。<br /><br /> 提示：您可以在 targets 檔中指定相對於 targets 檔 (而不是相對於原始專案檔) 的相對路徑。 |
| `MSBuildThisFileName` | 保留 | `MSBuildThisFileFullPath` 的檔案名稱部分，不包含副檔名。 |
| `MSBuildToolsPath` | 保留 | 與 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 的值相關聯之 `MSBuildToolsVersion` 版本的安裝路徑。<br /><br /> 不要在路徑中包含結尾的反斜線。<br /><br /> 這個屬性無法覆寫。 |
| `MSBuildToolsVersion` | 保留 | 用來建置專案的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工具組版本。<br /><br /> 注意:[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 工具組包含用於建置應用程式的工作、目標和工具。 工具包括編譯器，例如 *csc.exe* 和 vbc.exe。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 及[標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)。 |

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
* 選擇
* When
* Otherwise

## <a name="see-also"></a>另請參閱
- [MSBuild 參考](../msbuild/msbuild-reference.md)

- [MSBuild 屬性](../msbuild/msbuild-properties.md)
