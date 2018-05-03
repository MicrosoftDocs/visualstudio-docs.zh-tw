---
title: 自訂組建 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea021decfc0940ecaaedde2ecfdde34db833b86
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="customize-your-build"></a>自訂組建

使用標準建置程序 (匯入 `Microsoft.Common.props` 和 `Microsoft.Common.targets`) 的 MSBuild 專案有幾個擴充性攔截程序，可以用來自訂您的建置程序。

## <a name="adding-arguments-to-command-line-msbuild-invocations-for-your-project"></a>將引數新增至專案的命令列 MSBuild 引動過程

來源目錄中或其上的 `Directory.Build.rsp` 檔案將會套用到專案的命令列組建。 如需詳細資料，請參閱 [MSBuild 回應檔](../msbuild/msbuild-response-files.md#directorybuildrsp)。

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props 和 Directory.Build.targets

在版本 15 之前的 MSBuild 版本中，如果您想要將新的自訂屬性提供給方案中的專案，則必須手動將該屬性的參考新增至方案中的每個專案檔。 或者，除此之外，您必須在 *.props* 檔案中定義屬性，然後明確地匯入方案之每個專案中的 *.props* 檔案。

不過，您現在可以使用一個步驟將新的屬性新增至每個專案，方法是將它定義在包含原始檔的根資料夾內稱為 *Directory.Build.props* 的單一檔案中。 執行 MSBuild 時，*Microsoft.Common.props* 會搜尋您的目錄結構中是否有 *Directory.Build.props* 檔案 (而且 *Microsoft.Common.targets* 會尋找 *Directory.Build.targets*)。 如果找到，則會匯入屬性。 *Directory.Build.props* 是使用者定義的檔案，可讓您自訂目錄下的專案。

### <a name="directorybuildprops-example"></a>Directory.Build.props 範例

例如，如果您想要讓所有專案存取新的 Roslyn **/deterministic** 功能 (透過 `$(Deterministic)` 屬性公開於 Roslyn `CoreCompile` 目標中)，則可以執行下列動作。

1. 在存放庫根目錄中建立稱為 *Directory.Build.props* 的新檔案。
2. 將下列 XML 新增至檔案。

  ```xml
  <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
  </Project>
  ```
3. 執行 MSBuild。 您專案之 *Microsoft.Common.props* 和 *Microsoft.Common.targets* 的現有匯入會找到檔案，並將它匯入。

### <a name="search-scope"></a>搜尋範圍

搜尋 *Directory.Build.props* 檔案時，MSBuild 會從專案位置 (`$(MSBuildProjectFullPath)`) 往上逐步瀏覽目錄結構，並在找到 *Directory.Build.props* 檔案之後停止。 例如，如果您的 `$(MSBuildProjectFullPath)` 是 *c:\users\username\code\test\case1*，則 MSBuild 會在該處開始搜尋，然後往上搜尋目錄結構，直到找到下列目錄結構中的 *Directory.Build.props* 檔案。

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

方案檔的位置與 *Directory.Build.props* 無關。

### <a name="import-order"></a>匯入順序

在 *Microsoft.Common.props* 中，因為 *Directory.Build.props* 很早就會被匯入，所以它無法使用較晚才定義的屬性。 因此，請避免參考尚未定義的屬性 (因此會評估為空的)。

從 NuGet 套件匯入 *.targets* 檔案之後，會從 *Microsoft.Common.targets* 匯入 *Directory.Build.targets*。 因此，它可以用來覆寫大部分組建邏輯中所定義的屬性和目標，但有時可能需要在最後匯入之後於專案檔內執行自訂。

### <a name="use-case-multi-level-merging"></a>使用案例：多層級合併

假設您有這種標準方案結構：

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

使用者可能需要所有專案 *(1)* 的通用屬性、*src* 專案 *(2-src)* 的通用屬性和 *test* 專案 *(2-test)* 的通用屬性。

若要讓 MSBuild 正確合併「內部」檔案 (*2-src* 和 *2-test*) 與「外部」檔案 (*1*)，您必須注意，一旦 MSBuild 找到 *Directory.Build.props* 檔案，就會停止進一步掃描。 若要繼續掃描並合併至外部檔案，請將此項目放入這兩個內部檔案中：

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild 的一般方法摘要如下：

- 針對任何指定的專案，MSBuild 會在方案結構中向上尋找第一個 *Directory.Build.props*，再將它與預設值合併，然後停止進一步掃描
- 如果您想要找到多個層級並加以合併，請從「內部」檔案對「外部」檔案進行 [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) 作業 (如上所示)
- 如果「外部」檔案本身不會在其上匯入任何項目，掃描就會到此停止
- 若要控制掃描/合併程序，請使用 `$(DirectoryBuildPropsPath)` 和 `$(ImportDirectoryBuildProps)`

或更簡單的做法：第一個不會匯入任何項目的 *Directory.Build.props*，則為 MSBuild 停止的位置。

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

根據預設，`Microsoft.Common.props` 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`，而 `Microsoft.Common.targets` 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`。 `MSBuildProjectExtensionsPath` 的預設值是 `$(BaseIntermediateOutputPath)` (`obj/`)。 這是 NuGet 用來參考套件所傳遞之組建邏輯的機制；亦即，在還原時，它會建立參考套件內容的 `{project}.nuget.g.props` 檔案。

您可以停用此擴充性機制，方法是在 `Directory.Build.props` 中或匯入 `Microsoft.Common.props` 之前，將 `ImportProjectExtensionProps` 屬性設定為 `false`。

> [!NOTE]
> 停用 MSBuildProjectExtensionsPath 匯入會導致 NuGet 套件所傳遞的組建邏輯無法套用到您的專案。 部分 NuGet 套件需要建置邏輯來執行其函式，若停用此項目則會變成沒有用處。

## <a name="user-file"></a>.user 檔案

Microsoft.Common.CurrentVersion.targets 會匯入 `$(MSBuildProjectFullPath).user` (如果存在的話)，因此您可以在專案旁建立含有這個額外延伸模組的檔案。 對於想要存回原始檔控制的長期變更，最好是變更專案本身，如此維護人員未來就不需要知道這個擴充機制。

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath 和 MSBuildUserExtensionsPath

> [!WARNING]
> 使用這些擴充機制，會使您更難以取得跨電腦的可重複組建。 請嘗試使用可存回原始檔控制系統，並可在程式碼基底的所有開發人員之間共用的組態。

依照慣例，許多核心組建邏輯檔案會在其內容之前匯入

```
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

，並在之後匯入

```
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

。 這可讓已安裝的 SDK 擴增常見專案類型的組建邏輯。

會在 `$(MSBuildUserExtensionsPath)` 中搜尋相同的目錄結構，這是每位使用者的資料夾 `%LOCALAPPDATA%\Microsoft\MSBuild`。 放置在該資料夾中的檔案，會針對該使用者認證下執行的對應專案類型的所有組建進行匯入。 藉由使用 `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` 模式設定在匯入檔案後指定　的屬性，即可停用使用者延伸模組。 例如，將 `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` 設定為 `false` 可防止匯入 `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`。

## <a name="customizing-the-solution-build"></a>自訂方案組建

> [!IMPORTANT]
> 以這種方式自訂方案組建只適用於使用 `MSBuild.exe` 的命令列組建。 它**不**適用於 Visual Studio 內的組建。

MSBuild 在建置方案檔時，會先在內部將其轉換成專案檔，再建置該檔案。 產生的專案檔會在定義任何目標之前匯入 `before.{solutionname}.sln.targets`，並在匯入目標之後匯入 `after.{solutionname}.sln.targets`，包括安裝到 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` 和 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` 目錄的目標。

例如，您可以在建置 `MyCustomizedSolution.sln` 之後，定義新的目標來寫入自訂記錄訊息，方法是在名為 `after.MyCustomizedSolution.sln.targets` 的相同目錄中建立一個檔案，其中包含：

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>請參閱

 [MSBuild 概念](../msbuild/msbuild-concepts.md) [MSBuild 參考](../msbuild/msbuild-reference.md)
