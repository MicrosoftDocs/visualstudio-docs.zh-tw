---
title: 自訂組建 | Microsoft Docs
description: 深入瞭解您可以用來自訂使用標準組建程式之 MSBuild 專案的數個擴充性勾點。
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2d533e4b7f275a70d20be684fbd781d62a3a109
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877353"
---
# <a name="customize-your-build"></a>自訂組建

使用標準建置程序 (匯入 Microsoft.Common.props 和 Microsoft.Common.targets) 的 MSBuild 專案有幾個擴充性攔截程序，可以用來自訂您的建置程序。

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>將引數新增至專案的命令列 MSBuild 引動過程

來源目錄中或其上的 *Directory.Build.rsp* 檔案將會套用到專案的命令列組建。 如需詳細資料，請參閱 [MSBuild 回應檔](../msbuild/msbuild-response-files.md#directorybuildrsp)。

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props 和 Directory.Build.targets

在 MSBuild 第 15 版之前，如果您想要將新的自訂屬性提供給方案中的專案，則必須手動將該屬性的參考新增至方案中的每個專案檔。 或者，您必須在 *.props* 檔中定義屬性，然後在方案中的每個專案中明確匯入 *.props* 檔案，還有其他事項。

不過，您現在可以使用一個步驟將新的屬性新增至每個專案，方法是將它定義在包含原始檔的根資料夾內稱為 *Directory.Build.props* 的單一檔案中。 當 MSBuild 執行時， *.props* 會在目錄結構中搜尋目錄 *。 .props* 檔案 *(和* 檔案會 *尋找) 的目錄。* 如果找到，則會匯入屬性。 *.Props* 是使用者定義的檔案，可提供目錄下專案的自訂。

> [!NOTE]
> 以 Linux 為基礎的檔案系統會區分大小寫。 請確定 Directory.Build.props 檔案名稱的大小寫完全相符，否則在建置過程中將不會偵測到。
>
> 如需詳細資訊，請參閱[此 GitHub 問題](https://github.com/dotnet/core/issues/1991#issue-368441031)。

### <a name="directorybuildprops-example"></a>Directory.Build.props 範例

例如，如果您想要讓所有專案存取新的 Roslyn **/deterministic** 功能 (透過 `$(Deterministic)` 屬性公開於 Roslyn `CoreCompile` 目標中)，則可以執行下列動作。

1. 在存放庫根目錄中建立名為 *.props* 的新檔案。
2. 將下列 XML 新增至檔案。

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```

3. 執行 MSBuild。 您專案的 *.props* 和 *microsoft* 的現有匯入會尋找檔案並加以匯入。

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

方案檔的位置與 *.props* 無關。

### <a name="import-order"></a>匯入順序

在 *Microsoft.Common.props* 中，*Directory.Build.props* 很早就會被匯入，因此它無法使用較晚才定義的屬性。 因此，請避免參考尚未定義的屬性 (將會評估為空的)。

在 *.props* 中設定的屬性可以在專案檔或匯入檔案中的其他位置覆寫，因此您應該將 *.props* 中的設定視為指定專案的預設值。

從 NuGet 套件匯入 *.targets* 檔案之後，將會從 *Microsoft* 匯入 *目錄。* 因此，它可以覆寫大部分組建邏輯中所定義的屬性和目標，或設定所有專案的屬性，不論個別專案的設定為何。

當您需要針對覆寫任何先前設定的個別專案設定屬性或定義目標時，請將該邏輯放在專案檔中，然後再進行最後的匯入。 若要在 SDK 樣式專案中這麼做，您必須先將 SDK 樣式屬性取代為對等的匯入。 請參閱 [如何使用 MSBuild 專案 sdk](how-to-use-project-sdk.md)。

> [!NOTE]
> 在評估期間，MSBuild 引擎會先讀取所有匯入的檔案，然後再開始執行任何專案的組建 (包括任何 `PreBuildEvent`) ，因此這些檔案不應該由 `PreBuildEvent` 或任何其他部分的組建進程修改。 除非下一個 *MSBuild.exe* 或下一個 Visual Studio 組建的調用，否則任何修改都不會生效。

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
- 如果您想要尋找併合並多個層級，則 [`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove) (上面顯示) 「內部」檔案中的「外部」檔案
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

根據預設，*Microsoft.Common.props* 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`，而 *Microsoft.Common.targets* 會匯入 `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`。 `MSBuildProjectExtensionsPath` 的預設值是 `$(BaseIntermediateOutputPath)` (`obj/`)。 NuGet 使用此機制來參考套件所傳遞的組建邏輯；亦即，在還原時，它會建立參考套件內容的 `{project}.nuget.g.props` 檔案。

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
> 以這種方式自訂方案組建只適用於使用 *MSBuild.exe* 的命令列建置。 它 **不** 適用於 Visual Studio 內的組建。 基於這個理由，不建議您在解決方案層級放置自訂。 自訂方案中所有專案的較佳替代方式，就是使用 [方案] 資料夾中的 *.props* 和 *目錄. 組建* 檔案，如本文中的其他內容所述。

MSBuild 在建置方案檔時，會先在內部將其轉換成專案檔，再建置該檔案。 產生的專案檔會在定義任何目標之前匯入 `before.{solutionname}.sln.targets`，並在匯入目標之後匯入 `after.{solutionname}.sln.targets`，包括安裝到 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` 和 `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter` 目錄的目標。

例如，您可以在建置 *MyCustomizedSolution.sln* 之後，定義新的目標來寫入自訂記錄訊息，方法是在名為 after.MyCustomizedSolution.sln.targets 的相同目錄中建立一個檔案，其中包含：

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

方案組建與專案組建不同，因此此處的設定不會影響專案組建。

## <a name="customize-all-net-builds"></a>自訂所有 .NET 組建

維護組建伺服器時，您可能需要為伺服器上的所有組建全域設定 MSBuild 設定。  基本上，您可以 *修改通用的* *.props* 檔案，但有更好的方法。」 您可以影響特定專案類型的所有組建 (例如，所有的 c # 專案) 使用特定的 MSBuild 屬性，以及新增特定的自訂 `.targets` 和檔案 `.props` 。

若要影響由 MSBuild 或 Visual Studio 的安裝所控管的所有 c # 或 Visual Basic 組建，建立 *自訂的檔案：在* microsoft 之前或 *自訂* 之前，將在 *microsoft* 之前或之後執行的目標。例如，在 microsoft 之前或之後、 *.props* 或自訂之前，將會在 .props 之前或之後進行處理。 *.props* 的屬性會在之前或之後處理。

您可以使用下列 MSBuild 屬性來指定這些檔案的位置：

- CustomBeforeMicrosoftCommonProps
- CustomBeforeMicrosoftCommonTargets
- CustomAfterMicrosoftCommonProps
- CustomAfterMicrosoftCommonTargets
- CustomBeforeMicrosoftCSharpProps
- CustomBeforeMicrosoftVisualBasicProps
- CustomAfterMicrosoftCSharpProps
- CustomAfterMicrosoftVisualBasicProps
- CustomBeforeMicrosoftCSharpTargets
- CustomBeforeMicrosoftVisualBasicTargets
- CustomAfterMicrosoftCSharpTargets
- CustomAfterMicrosoftVisualBasicTargets

這些屬性的 *通用* 版本會影響 c # 和 Visual Basic 專案。 您可以在 MSBuild 命令列中設定這些屬性。

```cmd
msbuild /p:CustomBeforeMicrosoftCommonTargets="C:\build\config\Custom.Before.Microsoft.Common.Targets" MyProject.csproj
```

最佳方法取決於您的案例。 使用 Visual Studio 擴充性，您可以自訂群組建系統，並提供安裝和管理自訂的機制。

如果您有專用的組建伺服器，而且想要確保特定目標一律會在該伺服器上執行之適當專案類型的所有組建上執行，則使用全域自訂 `.targets` 或檔案 `.props` 會有意義。  如果您只想要在特定條件套用時執行自訂目標，請使用另一個檔案位置，並在 MSBuild 命令列中設定適當的 MSBuild 屬性，以便在必要時設定該檔案的路徑。

> [!WARNING]
> Visual Studio 會使用自訂或檔案， `.targets` `.props` 如果在 MSBuild 資料夾中找到任何相符型別的專案時，就會使用這些檔案。 這可能會產生非預期的結果，如果不正確地執行，則可以停用 Visual Studio 在您的電腦上建立的能力。

## <a name="customize-c-builds"></a>自訂 c + + 組建

針對 c + + 專案，先前提及的自訂 *.targets* 和 *. .props* 檔案無法以覆寫預設設定的相同方式來使用。 *目錄. 組建。 .props* 是由 *.props* 匯入，但 `Microsoft.Cpp.Default.props` 大部分的預設值都是在 *.props* 中定義，而針對某些屬性，則無法使用「如果尚未定義」條件，因為已定義了屬性，但在中定義的特定專案屬性必須有不同的預設值，但 `PropertyGroup` `Label="Configuration"` (參閱 [.vcxproj 和 .props 檔案結構](/cpp/build/reference/vcxproj-file-structure)) 。

但是，您可以使用下列屬性來指定要在 *.props* 檔案 () s，以在 *Microsoft \* .cpp* 之前/之後自動匯入。檔案：

- ForceImportAfterCppDefaultProps
- ForceImportBeforeCppProps
- ForceImportAfterCppProps
- ForceImportBeforeCppTargets
- ForceImportAfterCppTargets

若要自訂所有 c + + 組建的預設屬性值，請建立另一個 *.props* 檔案， (說， *myprops.props. .Props*) ，然後在指向它的情況下定義 `ForceImportAfterCppProps` 屬性 `Directory.Build.props` ：

<PropertyGroup><ForceImportAfterCppProps>$ (MsbuildThisFileDirectory) \myprops.props<ForceImportAfterCppProps>
</PropertyGroup>

*Myprops.props* 會在 *.props* 的最一端自動匯入 .props。

## <a name="customize-all-c-builds"></a>自訂所有 c + + 組建

不建議自訂 Visual Studio 安裝，因為不容易追蹤這類自訂專案，但是如果您要擴充 Visual Studio 以自訂特定平臺的 c + + 組建，您可以建立 `.targets` 每個平臺的檔案，並將它們放在適用于這些平臺的適當匯入資料夾中，作為 Visual Studio 擴充功能的一部分。

`.targets`Win32 平臺的檔案（如下所示）包含下列 `Import` 元素：

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportBefore\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportBefore')"
/>
```

相同檔案的結尾附近有類似的元素：

```xml
<Import Project="$(VCTargetsPath)\Platforms\Win32\ImportAfter\*.targets"
        Condition="Exists('$(VCTargetsPath)\Platforms\Win32\ImportAfter')"
/>
```

*%ProgramFiles32%\MSBuild\Microsoft.Cpp\v {version} \ 平臺中的其他目標平臺有類似的匯入元素 \* 。

當您根據平臺將檔案放在適當的資料夾中時，MSBuild 會將您的檔案匯入 `.targets` `ImportAfter` 該平臺的每個 c + + 組建中。 如有需要，您可以在該處放入多個檔案 `.targets` 。 

您可以使用 Visual Studio 的擴充性，進一步自訂，例如定義新平臺。 如需詳細資訊，請參閱 [c + + 專案](../extensibility/visual-cpp-project-extensibility.md)擴充性。

### <a name="specify-a-custom-import-on-the-command-line"></a>在命令列上指定自訂匯入

針對 `.targets` 您想要包含給 c + + 專案特定組建的自訂，請 `ForceImportBeforeCppTargets` `ForceImportAfterCppTargets` 在命令列上設定一或兩個屬性。

```cmd
msbuild /p:ForceImportBeforeCppTargets="C:\build\config\Custom.Before.Microsoft.Cpp.Targets" MyCppProject.vcxproj
```

針對全域設定 (會影響組建伺服器上平臺的所有 c + + 組建) ，有兩種方法。 首先，您可以使用一律設定的系統內容變數來設定這些屬性。 這是可行的，因為 MSBuild 一律會讀取環境並建立 (或覆寫所有環境變數) 屬性。

## <a name="see-also"></a>另請參閱

- [MSBuild 概念](../msbuild/msbuild-concepts.md)

- [MSBuild 參考](../msbuild/msbuild-reference.md)
