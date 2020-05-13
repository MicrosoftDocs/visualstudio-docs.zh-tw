---
title: 自訂組建 | Microsoft Docs
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7ddf87f5fa9f937c0272e37f3a6b4aba29f2d6c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77652790"
---
# <a name="customize-your-build"></a>自訂組建

使用標準建置程序 (匯入 Microsoft.Common.props** 和 Microsoft.Common.targets**) 的 MSBuild 專案有幾個擴充性攔截程序，可以用來自訂您的建置程序。

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>將引數新增至專案的命令列 MSBuild 引動過程

來源目錄中或其上的 *Directory.Build.rsp* 檔案將會套用到專案的命令列組建。 如需詳細資料，請參閱 [MSBuild 回應檔](../msbuild/msbuild-response-files.md#directorybuildrsp)。

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props 和 Directory.Build.targets

在 MSBuild 第 15 版之前，如果您想要將新的自訂屬性提供給方案中的專案，則必須手動將該屬性的參考新增至方案中的每個專案檔。 或者，您必須在 *.props*檔中定義屬性，然後顯式導入解決方案中的每個專案中的 *.props*檔，等等。

不過，您現在可以使用一個步驟將新的屬性新增至每個專案，方法是將它定義在包含原始檔的根資料夾內稱為 *Directory.Build.props* 的單一檔案中。 MSBuild 運行時 *，Microsoft.Common.props*會搜索目錄結構，查找*目錄.Build.props*檔（和*Microsoft.Common.target）* 查找*目錄.Build.target。* 如果找到，則會匯入屬性。 *目錄.Build.props*是一個使用者定義的檔，為目錄下的專案提供自訂。

> [!NOTE]
> 以 Linux 為基礎的檔案系統會區分大小寫。 請確定 Directory.Build.props 檔案名稱的大小寫完全相符，否則在建置過程中將不會偵測到。
>
> 如需詳細資訊，請參閱[此 GitHub 問題](https://github.com/dotnet/core/issues/1991#issue-368441031)。

### <a name="directorybuildprops-example"></a>Directory.Build.props 範例

例如，如果您想要讓所有專案存取新的 Roslyn **/deterministic** 功能 (透過 `$(Deterministic)` 屬性公開於 Roslyn `CoreCompile` 目標中)，則可以執行下列動作。

1. 在名為*Directory.Build.props*的回購根目錄中創建新檔。
2. 將下列 XML 新增至檔案。

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. 執行 MSBuild。 您的專案現有的*Microsoft.Common.props*和*Microsoft.Common.targets*的導入會找到該檔並導入它。

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

解決方案檔的位置與*目錄無關。*

### <a name="import-order"></a>匯入順序

在 *Microsoft.Common.props* 中，*Directory.Build.props* 很早就會被匯入，因此它無法使用較晚才定義的屬性。 因此，請避免參考尚未定義的屬性 (將會評估為空的)。

*目錄.Build.target*是從*Microsoft.Common.target*導入 NuGet 包後導入*的.target*檔。 因此，它可以覆寫大部分組建邏輯中所定義的屬性和目標，但有時可能需要在最後匯入之後自訂專案檔。

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

若要讓 MSBuild 正確合併「內部」檔案 (*2-src* 和 *2-test*) 與「外部」檔案 (*1*)，您必須注意，一旦 MSBuild 找到 *Directory.Build.props* 檔案，就會停止進一步掃描。 若要繼續掃描並合併至外部檔案，請將此程式碼放入這兩個內部檔案中：

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

MSBuild 的一般方法摘要如下：

- 針對任何指定的專案，MSBuild 會在方案結構中向上尋找第一個 *Directory.Build.props*，再將它與預設值合併，然後停止進一步掃描
- 如果希望找到併合並多個級別，則[`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove)（如上圖所示）來自"內部"檔中的"外部"檔
- 如果「外部」檔案本身不會在其上匯入任何項目，掃描就會到此停止
- 若要控制掃描/合併程序，請使用 `$(DirectoryBuildPropsPath)` 和 `$(ImportDirectoryBuildProps)`

或更簡單的做法：第一個不會匯入任何項目的 *Directory.Build.props*，則為 MSBuild 停止的位置。

### <a name="choose-between-adding-properties-to-a-props-or-targets-file"></a>選擇將屬性加入 .props 或是 .targets 檔案

MSBuild 需相依於匯入順序，且屬性的最後一個定義 (或是 `UsingTask` 或目標) 將會是系統所使用的定義。

使用明確匯入時，您可以在任何時間點從 *.props* 或 *.targets* 檔案匯入。 以下是廣泛使用的慣例：

- *.props* 檔案會以較早的匯入順序匯入。

- *.targets* 檔案會以較晚的匯入順序匯入。

此慣例會由 `<Project Sdk="SdkName">` 匯入強制執行 (也就是 *Sdk.props* 的匯入會在該檔案所有內容之前先發生，而 *Sdk.targets* 則會在檔案的所有內容之後最後發生)。

決定要將屬性置於何處時，請使用下列一般指導方針：

- 針對許多屬性，其被定義的位置本身並不重要，因為它們不會被覆寫，且在執行階段會變成唯讀。

- 針對可能會在個別專案中自訂的行為，請將預設值設定在 *.props* 檔案中。

- 透過讀取可能的自訂屬性來避免在 *.props* 檔案中設定相依屬性，因為在 MSBuild 讀取使用者的專案之前，自訂將不會發生。

- 在 *.targets* 檔案中設定相依屬性，因為它們將會從個別專案中取得自訂項目。

- 如果您需要覆寫屬性，請在所有使用者專案自訂皆有機會生效之後，於 *.targets* 檔案中這麼做。 請謹慎使用衍生屬性；您可能也需要覆寫衍生屬性。

- 將項目包含在 *.props* 檔案中 (在屬性上設定條件)。 系統會在任何項目之前先考慮所有屬性，因此使用者專案屬性自訂項目會被收取，而這能讓使用者的專案有機會 `Remove` 或 `Update` 由匯入所引進的任何項目。

- 在 *.targets* 檔案中定義目標。 不過，如果 *.targets* 檔案是由 SDK 匯入，請記得此案例會使覆寫目標變得更為困難，因為使用者的專案預設並沒有位置可以覆寫它。

- 可能的話，請盡量在評估期間自訂屬性，而非在目標內變更屬性。 此指導方針可讓載入專案並了解其進行情況的工作變得更加容易。

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

根據預設，*Microsoft.Common.props* 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`，而* Microsoft.Common.targets* 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`。 `MSBuildProjectExtensionsPath` 的預設值是 `$(BaseIntermediateOutputPath)` (`obj/`)。 NuGet 使用此機制來參考套件所傳遞的組建邏輯；亦即，在還原時，它會建立參考套件內容的 `{project}.nuget.g.props` 檔案。

您可以將 *Directory.Build.props* 中的 `ImportProjectExtensionProps` 屬性設定為 `false`，或在匯入 *Microsoft.Common.props* 之前，停用此擴充性機制。

> [!NOTE]
> 停用 MSBuildProjectExtensionsPath 匯入會導致 NuGet 套件所傳遞的組建邏輯無法套用到您的專案。 部分 NuGet 套件需要建置邏輯來執行其函式，若停用此項目則會變成沒有用處。

## <a name="user-file"></a>.user 檔案

*Microsoft.Common.CurrentVersion.targets* 會匯入 `$(MSBuildProjectFullPath).user` (若存在的話)，因此您可以在專案旁建立含有這個額外延伸模組的檔案。 對於想要存回原始檔控制的長期變更，最好是變更專案本身，如此維護人員未來就不需要知道這個擴充機制。

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath 和 MSBuildUserExtensionsPath

> [!WARNING]
> 使用這些擴充機制，會使您更難以取得跨電腦的可重複組建。 請嘗試使用可存回原始檔控制系統，並可在程式碼基底的所有開發人員之間共用的組態。

依照慣例，許多核心組建邏輯檔案會在其內容之前匯入

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

，並在之後匯入

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

。 此慣例可讓已安裝的 SDK 擴增常見專案類型的組建邏輯。

會在 `$(MSBuildUserExtensionsPath)` 中搜尋相同的目錄結構，這是每位使用者的資料夾 *%LOCALAPPDATA%\Microsoft\MSBuild*。 放置在該資料夾中的檔案，會針對該使用者認證下執行的對應專案類型的所有組建進行匯入。 使用 `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}` 模式設定在匯入檔案後指定的屬性，即可停用使用者延伸模組。 例如，將 `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` 設定為 `false` 可防止匯入 `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`。

## <a name="customize-the-solution-build"></a>自訂方案組建

> [!IMPORTANT]
> 以這種方式自訂方案組建只適用於使用 *MSBuild.exe* 的命令列建置。 它**不**適用於 Visual Studio 內的組建。

MSBuild 在建置方案檔時，會先在內部將其轉換成專案檔，再建置該檔案。 產生的專案檔會在定義任何目標之前匯入 `before.{solutionname}.sln.targets`，並在匯入目標之後匯入 `after.{solutionname}.sln.targets`，包括安裝到 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` 和 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` 目錄的目標。

例如，您可以在建置 *MyCustomizedSolution.sln* 之後，定義新的目標來寫入自訂記錄訊息，方法是在名為 after.MyCustomizedSolution.sln.targets** 的相同目錄中建立一個檔案，其中包含：

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="customize-all-net-builds"></a>自訂所有 .NET 生成

維護生成伺服器時，您可能需要全域佈建服務器上的所有生成設置的 MSBuild 設置。  原則上，你可以修改全球*微軟.Common.Targets*或*微軟.Common.Props*檔，但有一個更好的方法。 通過使用某些 MSBuild 屬性並添加某些自訂`.targets`和`.props`檔，可以影響特定專案類型（如所有 C# 專案）的所有生成。

要影響所有由 MSBuild 或 Visual Studio 的安裝管理的所有 C# 或視覺化基本構建，請創建一個檔*自訂.以前.Microsoft.Common.Target*或*自訂.後.Microsoft.Common.Target*的目標，目標將在*Microsoft.Common.target*或檔自訂之前或之後運行。*之前.Microsoft.Common.Props.after.Microsoft.Common.props.，* 其屬性將在*Microsoft.Common.prop.* *Custom.After.Microsoft.Common.Props*

可以使用以下 MSBuild 屬性指定這些檔的位置：

- 自訂前微軟公共道具
- CustomBeforeMicrosoftCommonTargets
- 自訂後微軟公共道具
- 自訂後微軟公共目標
- 自訂前微軟C夏普
- 自訂前微軟視覺基礎道具
- 自訂後微軟C夏普
- 自訂後微軟視覺基礎道具
- 自訂前微軟C夏普目標
- 自訂之前微軟視覺基本目標
- 自訂後微軟C夏普目標
- 自訂後微軟視覺基本目標

這些屬性*的通用*版本同時影響 C# 和視覺化基本專案。 您可以在 MSBuild 命令列中設置這些屬性。

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

最佳方法取決於您的方案。 如果您有專用生成伺服器，並且希望確保某些目標始終在該伺服器上執行的相應專案類型的所有生成上執行，則使用全域自訂`.targets`或`.props`檔是有意義的。  如果希望自訂目標僅在應用某些條件時執行，則使用另一個檔位置，並通過僅在需要時在 MSBuild 命令列中設置相應的 MSBuild 屬性來設置該檔的路徑。

> [!WARNING]
> Visual Studio 使用`.targets`自訂`.props`或檔，如果它在 MSBuild 資料夾中找到它們，則每當它生成匹配類型的任何專案時。 這會產生意外的後果，如果處理不正確，可能會禁用 Visual Studio 在電腦上構建的能力。

## <a name="customize-all-c-builds"></a>自訂所有C++生成

對於C++專案，將忽略前面提到的`.targets`自訂`.props`和檔。 對於C++專案，您可以為每個平臺`.targets`創建檔，並將它們放在這些平臺的相應導入資料夾中。

Win32 平臺`.targets`*的 Microsoft.Cpp.Win32.target*的檔包含以下`Import`元素：

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

同一檔的末尾有一個類似的元素：

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

在 [%程式檔32%]MSBuild_Microsoft.Cpp_v_Platform 中，其他目標平臺存在類似的導入元素\*。

根據平臺將`.targets`檔放入相應的資料夾中後，MSBuild 會將檔導入該平臺的每個C++生成。 如果需要，可以放置`.targets`多個檔。

### <a name="specify-a-custom-import-on-the-command-line"></a>在命令列上指定自訂導入

對於要`.targets`為C++專案的特定生成包括的自訂，請在命令列`ForceImportBeforeCppTargets``ForceImportAfterCppTargets`上設置一個或兩個屬性。

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

對於全域設置（例如，要影響生成伺服器上的平臺的所有C++生成），有兩種方法。 首先，可以使用始終設置的系統內容變數設置這些屬性。 這之所以有效，是因為 MSBuild 始終讀取環境並為所有環境變數創建（或重寫）屬性。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)

- [MSBuild 參考](../msbuild/msbuild-reference.md)
