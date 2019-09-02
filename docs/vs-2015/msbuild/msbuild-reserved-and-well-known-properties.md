---
title: MSBuild 保留和已知屬性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181087"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild 保留和已知屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 提供一組預先定義的屬性，用來儲存專案檔和 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 二進位檔的相關資訊。 這些屬性的評估方式與其他 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 屬性相同。 例如，若要使用 `MSBuildProjectFile` 屬性，請輸入 `$(MSBuildProjectFile)`。  
  
 MSBuild 會使用下表中的值預先定義保留和已知的屬性。 保留的屬性不能覆寫，但是已知的屬性可以使用同名的環境屬性、全域屬性或專案檔中宣告的屬性加以覆寫。  
  
## <a name="reserved-and-well-known-properties"></a>保留和已知屬性  
 下表將描述 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 預先定義的屬性。  
  
|屬性|說明|保留或已知|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|目前使用的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 二進位檔所在資料夾的絕對路徑 (例如 C:\Windows\Microsoft.Net\Framework\\*versionNumber*)。 如果您必須參考 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 目錄中的檔案，這個屬性會相當實用。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|保留|  
|`MSBuildExtensionsPath`|於 .NET Framework 4 中引入：`MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32` 兩者的預設值並無差異。 您可以將環境變數 `MSBUILDLEGACYEXTENSIONSPATH` 設定為非 null 值，藉此啟用舊版中 `MSBuildExtensionsPath` 之預設值的行為。<br /><br /> 在 .NET Framework 3.5 (含) 以前版本中，`MSBuildExtensionsPath` 的預設值會指向 \Program Files\ 或 \Program Files (x86) 資料夾下 MSBuild 子資料夾的路徑 (根據目前處理序的位元而定)。 例如，若是 64 位元電腦上的 32 位元處理序，這個屬性會指向 \Program Files (x86) 資料夾。 若是 64 位元電腦上的 64 位元處理序，這個屬性會指向 \Program Files 資料夾。<br /><br /> 不要在這個屬性中包含結尾的反斜線。<br /><br /> 這個位置是放置目標檔案的理想位置。 例如，您的目標檔案可以安裝於 \Program Files\MSBuild\MyFiles\Northwind.targets，然後使用下面這個 XML 程式碼匯入專案檔中：<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|已知|  
|`MSBuildExtensionsPath32`|\Program Files 或 \Program Files (x86) 資料夾下 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 子資料夾的路徑。 這個路徑永遠指向 32 位元電腦上的 32 位元 \Program Files 資料夾，以及 64 位元電腦上的 \Program Files (x86)。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath64`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|已知|  
`MSBuildExtensionsPath64`|\Program Files 資料夾下 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 子資料夾的路徑。 若是 64 位元電腦，這個路徑永遠指向 \Program Files 資料夾。 若是 32 位元電腦，這個路徑是空白的。 請參閱 `MSBuildExtensionsPath` 和 `MSBuildExtensionsPath32`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|已知|  
|`MSBuildLastTaskResult`|如果前述工作順利完成且沒有任何錯誤 (即使有警告)，則為 `true`，如果前述工作發生錯誤，則為 `false`。 通常在工作中發生錯誤時，錯誤會在該專案中最後發生。 因此，這個屬性的值絕不會是 `false`，但下列情節除外：<br /><br /> - 將 [Task 項目 (MSBuild)](../msbuild/task-element-msbuild.md) 的 `ContinueOnError` 屬性設為`WarnAndContinue` (或 `true`) 或 `ErrorAndContinue` 時。<br /><br /> - 當 `Target` 具有 [OnError 項目 (MSBuild)](../msbuild/onerror-element-msbuild.md) 做為子項目時。|保留|  
|`MSBuildNodeCount`|建置時使用的並行處理序數目上限。 這是您在命令列中為 **/maxcpucount** 指定的值。 如果您已指定 **/maxcpucount**，但未指定值，則 `MSBuildNodeCount` 會指定電腦中的處理器數目。 如需詳細資訊，請參閱[命令列參考](../msbuild/msbuild-command-line-reference.md)和[同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)。|保留|  
|`MSBuildProgramFiles32`|32 位元程式資料夾的位置，例如 `C:\Program Files (x86)`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|保留|  
|`MSBuildProjectDefaultTargets`|`DefaultTargets` 項目的 `Project` 屬性中所指定目標的完整清單。 例如，下列 `Project` 項目的 `MSBuildDefaultTargets` 屬性值為 `A;B;C`。<br /><br /> `<Project DefaultTargets="A;B;C" >`|保留|  
|`MSBuildProjectDirectory`|專案檔所在目錄的絕對路徑，例如 `C:\MyCompany\MyProduct`。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|保留|  
|`MSBuildProjectDirectoryNoRoot`|`MSBuildProjectDirectory` 屬性的值，不包含根磁碟機。<br /><br /> 不要在這個屬性中包含結尾的反斜線。|保留|  
|`MSBuildProjectExtension`|專案檔的副檔名，包括英文句號，例如 .proj。|保留|  
|`MSBuildProjectFile`|專案檔的完整檔名，包括副檔名，例如 MyApp.proj。|保留|  
|`MSBuildProjectFullPath`|專案檔的絕對路徑和完整檔名，包括副檔名，例如 C:\MyCompany\MyProduct\MyApp.proj。|保留|  
|`MSBuildProjectName`|專案檔的檔案名稱，不包括副檔名，例如 MyApp。|保留|  
|`MSBuildStartupDirectory`|呼叫 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 所在資料夾的絕對路徑。 使用這個屬性就可以在專案樹狀結構中建置特定點之下的所有項目，而不需要在每個目錄中建立 dirs.proj 檔案。 而您只會有一個專案，例如 c:\traversal.proj，如下所示：<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> 若要在樹狀結構中的任何點進行建置，請輸入：<br /><br /> `msbuild c:\traversal.proj`<br /><br /> 不要在這個屬性中包含結尾的反斜線。|保留|  
|`MSBuildThisFile`|`MSBuildThisFileFullPath` 的檔案名稱和副檔名部分。|保留|  
|`MSBuildThisFileDirectory`|`MSBuildThisFileFullPath` 的目錄部分。<br /><br /> 在路徑中包含結尾的反斜線。|保留|  
|`MSBuildThisFileDirectoryNoRoot`|`MSBuildThisFileFullPath` 的目錄部分，不包括根磁碟機。<br /><br /> 在路徑中包含結尾的反斜線。|保留|  
|`MSBuildThisFileExtension`|`MSBuildThisFileFullPath` 的副檔名部分。|保留|  
|`MSBuildThisFileFullPath`|包含執行中目標之專案檔或 targets 檔的絕對路徑。<br /><br /> 提示：您可以在目標檔案中指定相對於目標檔 (而不是相對於原始專案檔) 的相對路徑。|保留|  
|`MSBuildThisFileName`|`MSBuildThisFileFullPath` 的檔案名稱部分，不包含副檔名。|保留|  
|`MSBuildToolsPath`|與 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 的值相關聯之 `MSBuildToolsVersion` 版本的安裝路徑。<br /><br /> 不要在路徑中包含結尾的反斜線。<br /><br /> 這個屬性無法覆寫。|保留|  
|`MSBuildToolsVersion`|用來建置專案的 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工具組版本。<br /><br /> 注意：[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 工具組包含用於建置應用程式的工作、目標和工具。 工具包括編譯器，例如 csc.exe 和 vbc.exe。 如需詳細資訊，請參閱[工具組 (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) 及[標準和自訂工具組的組態](../msbuild/standard-and-custom-toolset-configurations.md)。|保留|  
  
## <a name="see-also"></a>另請參閱  
 [MSBuild 參考](../msbuild/msbuild-reference.md) [MSBuild 屬性](msbuild-properties1.md)
