---
title: Live Unit Testing 常見問題集
ms.date: 10/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing FAQ
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: ba231e6c203197518b75a7a8c0592f01bba4ffe9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591537"
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing 常見問題集

## <a name="supported-frameworks"></a>支援的架構

**Live Unit Testing 支援哪些測試架構，而且支援的最低版本為何？**

Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 其配接器與架構所支援的最小版本也列於表格中。 單元測試架構全都可從 NuGet.org 取得。

|測試架構  |Visual Studio 配接器最小版本  |架構最小版本  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio 版本 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter 版本 3.7.0 |NUnit 版本 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

如果您有參考 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的舊版 MSTest 測試專案，而您不想要移至較新的 MSTest NuGet 套件，請升級至 Visual Studio 2019 或 Visual Studio 2017。

在某些情況下，您可能需要明確地還原方案中的專案所參考的 NuGet 封裝，才能使 Live Unit Testing 運作。 您可以藉由執行解決方案的明確組建（從最上層 Visual Studio 功能表中選取 [**組建**] > [**重建解決方案**]）來還原封裝，或是以滑鼠右鍵按一下方案並選取 [**還原 NuGet 套件**]，然後再啟用即時單元測試。

## <a name="net-core-support"></a>.NET Core 支援

**Live Unit Testing 是否可以與 .NET Core 搭配使用？**

是， Live Unit Testing 可以與 .NET Core 和 .NET Framework 搭配使用。

## <a name="configuration"></a>組態

**當我開啟 Live Unit Testing 時，為什麼它不會運作？**

[輸出] 視窗（選取 [Live Unit Testing] 下拉式選時）應該會告訴您 Live Unit Testing 無法運作的原因。 Live Unit Testing 不會運作的可能原因如下：

- 如果方案中之專案所參考的 NuGet 封裝尚未還原，Live Unit Testing 將不會運作。 在開啟 Live Unit Testing 之前明確地建置方案，或是還原方案中的 NuGet 套件，應該就能解決此問題。

- 如果您在專案中使用以 MSTest 為基礎的測試，請務必移除對 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的參考，然後新增對最新 MSTest NuGet 套件的參考，`MSTest.TestAdapter` (至少需要版本 1.1.11) 和 `MSTest.TestFramework` (至少需要版本 1.1.11)。 如需詳細資訊，請參閱[使用 Visual Studio 中的 Live Unit Testing](live-unit-testing.md#supported-test-frameworks) 一文的＜支援的測試架構＞一節。

- 您的方案中應該至少要有一個專案含有參考 xUnit、NUnit 或 MSTest 測試架構的 NuGet 參考或直接參考。 此專案應該也要參考對應的 Visual Studio 測試配接器 NuGet 封裝。 Visual Studio 測試配接器也可以透過 *.runsettings* 檔案來參考。 *.runsettings* 檔案必須具有類似下列範例的項目：

```xml
<RunSettings>
    <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
     </RunConfiguration>
</RunSettings>
```

## <a name="incorrect-coverage-after-upgrade"></a>升級後不正確的涵蓋範圍

**為什麼您將 Visual Studio 專案中參考的測試配接器升級到支援版本之後，Live Unit Testing 顯示不正確的涵蓋範圍？**

- 如果解決方案中的多個專案參考 NuGet 測試配接器套件時，每個都必須升級為支援的版本。

- 請確定從測試配接器套件匯入的 MSBuild *.props* 檔案也正確地更新。 檢查 NuGet 套件版本/匯入路徑，這通常可以在接近專案檔上方找到，如下所示︰

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="customize-builds"></a>自訂組建

**我是否可以自訂 Live Unit Testing 組建？**

如果您的解決方案需要非「一般」非檢測組建所需的自訂步驟，以針對檢測設備 (Live Unit Testing) 進行建置，您可以將程式碼新增至專案或 *.targets* 檔案來檢查 `BuildingForLiveUnitTesting` 屬性，並執行自訂的建置前/後步驟。 您也可以根據這個專案屬性，選擇針對 Live Unit Testing 組建移除特定的建置步驟 (例如發佈或產生封裝)，或新增建置步驟 (例如複製必要條件)。 根據這個屬性自訂您的組建不會以任何方式更改您的一般組建，且只會影響 Live Unit Testing 組建。

例如，可能有一個目標會在一般建置期間產生 NuGet 封裝。 您可能不想讓 NuGet 封裝在每次進行編輯之後產生。 因此您可以執行類似下列的內容，在 Live Unit Testing 組建中停用該目標：  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-outputpath-outdir-or-intermediateoutputpath"></a>\<OutputPath >、\<OutDir > 或 \<IntermediateOutputPath 的錯誤訊息 >

**當 Live Unit Testing 嘗試建立我的解決方案時，為什麼會收到下列錯誤：「.。。似乎會無條件地設定 `<OutputPath>` 或 `<OutDir>`。Live Unit Testing 不會從輸出元件執行測試」？**

如果您的解決方案的組建程式具有指定應產生二進位檔之位置的自訂邏輯，您就會收到這個錯誤。 根據預設，二進位檔的位置取決於 `<OutputPath>`、`<OutDir>` 或 `<IntermediateOutputPath>`，以及 `<BaseOutputPath>` 或 `<BaseIntermediateOutputPath>`。

Live Unit Testing 會覆寫這些變數，以確保組建成品會卸載至 Live Unit Testing 成品資料夾，如果您的組建進程也會覆寫這些變數，則會失敗。

有兩個主要的方法可以成功建立 Live Unit Testing。 如需更輕鬆的組建設定，您可以將輸出路徑作為 `<BaseIntermediateOutputPath>`的基礎。 如需更複雜的設定，您可以 `<LiveUnitTestingBuildRootPath>`的輸出路徑作為基礎。

### <a name="overriding-outputpathintermediateoutputpath-conditionally-based-on-baseoutputpath-baseintermediateoutputpath"></a>根據 `<BaseOutputPath>`/ `<BaseIntermediateOutputPath>`，有條件地覆寫 `<OutputPath>`/`<IntermediateOutputPath>`。

> [!NOTE]
> 若要使用此方法，每個專案都必須能夠彼此獨立建立。 在組建期間，沒有另一個專案的專案參考成品。 在執行時間期間，沒有一個專案會從另一個專案動態載入元件（例如，呼叫 `Assembly.Loadfile("..\..\Project2\Release\Project2.dll")`）。

在組建期間，Live Unit Testing 會自動覆寫 `<BaseOutputPath>`/`<BaseIntermediateOutputPath>` 變數以作為 Live Unit Testing 成品資料夾的目標。

例如，如果您的組建會覆寫 <OutputPath>，如下所示：

```xml
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

則您可以使用下列 XML 來取代它：

```xml
<Project>
  <PropertyGroup>
    <BaseOutputPath Condition="'$(BaseOutputPath)' == ''">$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)\</BaseOutputPath>
    <OutputPath Condition="'$(OutputPath)' == ''">$(BaseOutputPath)</OutputPath>
  </PropertyGroup>
</Project>
```

這能確保 `<OutputPath>` 位於 `<BaseOutputPath>` 資料夾內。

請勿直接在建置流程中覆寫 `<OutDir>`，請改為覆寫 `<OutputPath>` 以將組建成品卸除到特定位置。

### <a name="overriding-your-properties-based-on-the-liveunittestingbuildrootpath-property"></a>根據 `<LiveUnitTestingBuildRootPath>` 屬性來覆寫屬性。

> [!NOTE]
> 在這種方法中，您必須謹慎處理在構件資料夾下新增的檔案，而這些檔案在組建期間不會產生。 下列範例顯示將 [封裝] 資料夾放置於 [成品] 底下時的執行動作。 由於在組建期間不會產生這個資料夾的內容，因此**不應該變更**MSBuild 屬性。

在 Live Unit Testing 組建期間，`<LiveUnitTestingBuildRootPath>` 屬性會設定為 Live Unit Testing 成品 資料夾的位置。

例如，假設您的專案有此處所示的結構。

```
.vs\...\lut\0\b
artifacts\{binlog,obj,bin,nupkg,testresults,packages}
src\{proj1,proj2,proj3}
tests\{testproj1,testproj2}
Solution.sln
```
在 Live Unit Testing 組建期間，`<LiveUnitTestingBuildRootPath>` 屬性會設定為 `.vs\...\lut\0\b`的完整路徑。 如果專案定義對應至方案目錄 `<ArtifactsRoot>` 屬性，您可以更新 MSBuild 專案，如下所示：

```xml
<Project>
    <PropertyGroup Condition="'$(LiveUnitTestingBuildRootPath)' == ''">
        <SolutionDir>$([MSBuild]::GetDirectoryNameOfFileAbove(`$(MSBuildProjectDirectory)`, `YOUR_SOLUTION_NAME.sln`))\</SolutionDir>

        <ArtifactsRoot>Artifacts\</ArtifactsRoot>
        <ArtifactsRoot Condition="'$(LiveUnitTestingBuildRootPath)' != ''">$(LiveUnitTestingBuildRootPath)</ArtifactsRoot>
    </PropertyGroup>

    <PropertyGroup>
        <BinLogPath>$(ArtifactsRoot)\BinLog</BinLogPath>
        <ObjPath>$(ArtifactsRoot)\Obj</ObjPath>
        <BinPath>$(ArtifactsRoot)\Bin</BinPath>
        <NupkgPath>$(ArtifactsRoot)\Nupkg</NupkgPath>
        <TestResultsPath>$(ArtifactsRoot)\TestResults</TestResultsPath>

        <!-- Note: Given that a build doesn't generate packages, the path should be relative to the solution dir, rather than artifacts root, which will change during a Live Unit Testing build. -->
        <PackagesPath>$(SolutionDir)\artifacts\packages</PackagesPath>
    </PropertyGroup>
</Project>
```

## <a name="build-artifact-location"></a>組建成品位置

**我想要 Live Unit Testing 組建的成品移至特定位置，而不是*vs*資料夾底下的預設位置。我該如何改變？**

將 `LiveUnitTesting_BuildRoot` 使用者層級環境變數設為您想要卸除 Live Unit Testing 組建成品的路徑。 

## <a name="test-explorer-versus-live-unit-testing"></a>測試瀏覽器與 Live Unit Testing

**從 [測試總管] 視窗執行測試，與在 Live Unit Testing 中執行測試有何不同？**

差異如下：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。 如果您想要偵錯已檢測的二進位檔，在您的測試方法中新增 [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) 方法呼叫會導致偵錯工具在每次執行該方法時 (包括 Live Unit Testing 執行該方法時) 啟動，您接著便可以附加已檢測的二進位檔，並對它進行偵錯。 不過，我們希望檢測設備在大部分的使用者案例中對您而言是透明的，且您不會需要對已檢測的二進位檔進行偵錯。

- Live Unit Testing 不會建立新的應用程式定義域來執行測試，但從 [測試總管] 視窗中執行的測試會建立新的應用程式定義域。

- Live Unit Testing 會循序執行每個測試組件中的測試。 在 [**測試瀏覽器**] 中，您可以選擇平行執行多個測試。

- [**測試瀏覽器**] 預設會在單一執行緒單元（STA）中執行測試，而 Live Unit Testing 會在多執行緒的公寓（MTA）中執行測試。 若要在 Live Unit Testing 於 STA 中執行 MSTest 測試，請利用可在 `MSTest.STAExtensions 1.0.3-beta` NuGet 封裝中找到的 `<STATestMethod>` 或 `<STATestClass>` 屬性，來裝飾測試方法或包含類別。 針對 NUnit，請使用 `<RequiresThread(ApartmentState.STA)>` 屬性來裝飾測試方法，而針對 xUnit，請使用 `<STAFact>` 屬性。

## <a name="exclude-tests"></a>排除測試

**如何從 Live Unit Testing 排除測試？**

請參閱[使用 Visual Studio 中的 Live Unit Testing](live-unit-testing.md#include-and-exclude-test-projects-and-test-methods) 一文章的＜包含和排除測試專案與測試方法＞一節，以了解使用者的特定設定。 若您想要針對特定的編輯工作階段執行一組特定的測試，或保存您個人的喜好設定，包含或排除測試非常有用。

針對方案特定的設定，您可以以程式設計方式套用 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 屬性，以排除方法、屬性、類別或結構，使 Live Unit Testing 不會檢測它們。 此外，您也可以在專案檔中將 `<ExcludeFromCodeCoverage>` 屬性設為 `true`，以排除對整個專案的檢測。 Live Unit Testing 仍然會執行尚未檢測的測試，但不會將它們的涵蓋範圍視覺化。

您也可以檢查是否已將 `Microsoft.CodeAnalysis.LiveUnitTesting.Runtime` 載入目前的應用程式定義域，並據以停用測試。 例如，您可以針對 xUnit 執行下列動作：

```csharp
[ExcludeFromCodeCoverage]
public class SkipLiveFactAttribute : FactAttribute
{
   private static bool s_lutRuntimeLoaded = AppDomain.CurrentDomain.GetAssemblies().Any(a => a.GetName().Name ==
                                            "Microsoft.CodeAnalysis.LiveUnitTesting.Runtime");
   public override string Skip => s_lutRuntimeLoaded ? "Test excluded from Live Unit Testing" : "";
}

public class Class1
{
   [SkipLiveFact]
   public void F()
   {
      Assert.True(true);
   }
}
```

::: moniker range="vs-2017"

## <a name="win32-pe-headers"></a>Win32 PE 標頭

**為什麼 Live Unit Testing 所建置之已檢測組件中的 Win32 PE 標頭會不一樣？**

此問題已修正，不存在於 Visual Studio 2017 15.3 版和更新版本中。

在舊版 Visual Studio 2017 中，有一個已知 Bug 可能會造成 Live Unit Testing 組建無法內嵌下列 Win32 PE 標頭資料：

- 檔案版本 (在程式碼中由 @System.Reflection.AssemblyFileVersionAttribute 指定)。

- Win32 圖示 (在命令列上由 `/win32icon:` 指定)。

- Win32 資訊清單 (在命令列上由 `/win32manifest:` 指定)。

透過 Live Unit Testing 執行時，依賴這些值的測試可能會失敗。

::: moniker-end

## <a name="continuous-builds"></a>連續組建

**為什麼 Live Unit Testing 會持續建置我的方案，即使我沒有做出任何編輯也一樣？**

即使組建程式產生的原始程式碼是解決方案本身的一部分，而且您的組建目標檔案沒有指定適當的輸入和輸出，您的解決方案還是可以建立。 您應該為目標提供輸入和輸出清單，讓 MSBuild 可以執行適當的更新狀態檢查，並判斷是否需要新的組建。

每當 Live Unit Testing 偵測到原始程式檔已變更時，即會開始建置。 因為您的方案組建會產生來源檔案，Live Unit Testing 進入無限的組建迴圈。 不過，如果在 Live Unit Testing 啟動第二個組建時，會檢查目標的輸入和輸出（從上一個組建中偵測到新產生的原始程式檔之後），它會中斷組建迴圈，因為輸入和輸出檢查會指出所有專案都是最新的。

## <a name="editor-icons"></a>編輯器圖示

**儘管根據輸出視窗中的訊息，Live Unit Testing 似乎正在執行測試，但為什麼我在編輯器中看不到任何圖示？**

如果 Live Unit Testing 正在運作的組件基於任何原因而未進行檢測，您可能在編輯器中看不到圖示。 例如，Live Unit Testing 與設定 `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` 的專案不相容。 在此情況下，您的建置流程需要更新以移除此設定，或將該設定變更為 `true`，Live Unit Testing 才能夠運作。 

## <a name="capture-logs"></a>擷取記錄

**如何收集更詳細的記錄以提出錯誤報告？**

您可以執行數個動作來收集更詳細的記錄：

- 移至 [工具] > [選項] > [Live Unit Testing]，然後將記錄選項變更為 [詳細資訊]。 詳細資訊記錄會使 [輸出] 視窗顯示更詳細的記錄。

- 將 `LiveUnitTesting_BuildLog` 使用者環境變數設為您想要用來擷取 MSBuild 記錄的檔案名稱。 然後就能從該檔案中擷取來自 Live Unit Testing 組建的詳細 MSBuild 記錄訊息。

- 將 `LiveUnitTesting_TestPlatformLog` 使用者環境變數設成 `1` 以擷取測試平台記錄檔。 然後就能從該 `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` 中擷取來自即時單元測試回合的詳細測試平台記錄訊息。

- 建立名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，並將它設為 1 (或任何值)，然後重新啟動 Visual Studio。 現在您應該會在 Visual Studio 的 [輸出 - 測試] 索引標籤中看見許多記錄。

## <a name="see-also"></a>請參閱

- [即時單元測試](live-unit-testing.md)
