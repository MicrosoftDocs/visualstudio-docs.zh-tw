---
title: "Live Unit Testing 常見問題集 | Microsoft Docs"
ms.date: 2017-10-03
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing FAQ
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2437a138e9e83d3b723971b53dac413ad0ea4151
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2018
---
# <a name="live-unit-testing-frequently-asked-questions"></a>Live Unit Testing 常見問題集

## <a name="live-unit-testing-is-improved-and-enhanced-regularly-how-can-i-find-information-about-the-latest-new-features-and-enhancements"></a>Live Unit Testing 會定期改善並增強。 如何找出最新功能和增強功能的相關資訊？

**答：**

若要了解從 Visual Studio 2017 15.3 版開始對 Live Unit Testing 進行的新功能和增強功能，請參閱 [Live Unit Testing 中的新功能](live-unit-testing-whats-new.md)。


## <a name="what-test-frameworks-does-live-unit-testing-support-and-what-are-the-minimum-supported-versions"></a>Live Unit Testing 支援哪些測試架構，而且支援的最低版本為何？

**答：**

Live Unit Testing 適用於下表所列的三種熱門單元測試架構。 其配接器與架構所支援的最小版本也列於表格中。 單元測試架構全都可從 NuGet.org 取得。

<table>
<tr>
   <th>測試架構</th>
   <th>Visual Studio 配接器最小版本</th>
   <th>架構最小版本</th>
</tr>
<tr>
   <td>xUnit.net</td>
   <td> xunit.runner.visualstudio 版本 2.2.0-beta3-build1187</td>
   <td>xunit 1.9.2</td>
</tr>
<tr>
   <td>NUnit</td>
   <td>NUnit3TestAdapter 版本 3.5.1</td>
   <td>NUnit 版本 3.5.0</td>
</tr>
<tr>
   <td>MSTest</td>
   <td>MSTest.TestAdapter 1.1.4-preview</td>
   <td>MSTest.TestFramework 1.0.5-preview</td>
</tr>
</table>

如果您的舊型 MSTest 測試專案參考 `Microsoft.VisualStudio.QualityTools.UnitTestFramework`，而且您不想要移至新版 MSTest NuGet 套件，請升級至 Visual Studio 2017 15.4 版。

在某些情況下，您可能需要明確地還原方案中的專案所參考的 NuGet 封裝，才能使 Live Unit Testing 運作。 若要執行此動作，您可以在啟用 Living Unit Testing 之前，明確地建置方案 (從最上層的 Visual Studio 功能表中依序選取 [建置] 和 [重建方案])，或是在方案中還原封裝 (以滑鼠右鍵按一下方案，然後選取 [還原 NuGet 封裝])。


## <a name="does-live-unit-testing-work-with-net-core"></a>Live Unit Testing 是否可以與 .NET Core 搭配使用？

**答：**

可以。 Live Unit Testing 可以與 .NET Core 和 .NET Framework 搭配使用。 在 Visual Studio 2017 版本 15.3 中，最近新增 .NET Core 支援。 如果您想要針對 .NET Core 的 Live Unit Testing 支援，請升級至此版本的 Visual Studio。

## <a name="why-doesnt-live-unit-testing-work-when-i-turn-it-on"></a>當我開啟 Live Unit Testing 時，為什麼它不會運作？

**答：**

[輸出] 視窗 (選取 Live Unit Testing 下拉式清單時) 應該會告訴您為什麼 Live Unit Testing 不會運作。 Live Unit Testing 不會運作的可能原因如下：

- 如果方案中之專案所參考的 NuGet 封裝尚未還原，Live Unit Testing 將不會運作。 在開啟 Live Unit Testing 之前明確地建置方案，或是還原方案中的 NuGet 封裝，應該就能解決此問題。

- 如果您在專案中使用以 MSTest 為基礎的測試，請務必移除對 `Microsoft.VisualStudio.QualityTools.UnitTestFramework` 的參考，然後新增對最新 MSTest NuGet 套件的參考，`MSTest.TestAdapter` (至少需要版本 1.1.11) 和 `MSTest.TestFramework` (至少需要版本 1.1.11)。 如需詳細資訊，請參閱[使用 Visual Studio 2017 Enterprise Edition 中的 Live Unit Testing](live-unit-testing.md#supported-test-frameworks) 主題中的＜支援的測試架構＞一節。

- 您的方案中應該至少要有一個專案含有參考 xUnit、NUnit 或 MSTest 測試架構的 NuGet 參考或直接參考。 此專案應該也要參考對應的 Visual Studio 測試配接器 NuGet 封裝。 Visual Studio 測試配接器也可以透過 `.runsettings` 檔案來參考。 `.runsettings` 檔案必須具有類似下列項目的項目：

   ```xml
    <RunSettings>
       <RunConfiguration>
          <TestAdaptersPaths>path-to-your-test-adapter</TestAdaptersPaths>
       </RunConfiguration>
    </RunSettings>
   ``` 

## <a name="why-does-live-unit-testing-show-incorrect-coverage-after-you-upgrade-the-test-adapter-referenced-in-your-visual-studio-projects-to-the-supported-version"></a>為什麼您將 Visual Studio 專案中參考的測試配接器升級到支援版本之後，Live Unit Testing 顯示不正確的涵蓋範圍？

**答：**

- 如果解決方案中的多個專案參考 NuGet 測試配接器套件時，每個都必須升級為支援的版本。

- 請確定從測試配接器套件匯入的 MSBuild .props 檔案也正確地更新。 檢查 NuGet 套件版本/匯入路徑，這通常可以在接近專案檔上方找到，如下所示︰

   ```xml
    <Import Project="..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props" Condition="Exists('..\packages\xunit.runner.visualstudio.2.2.0\build\net20\xunit.runner.visualstudio.props')" />
   ```

## <a name="can-i-customize-my-live-unit-testing-builds"></a>我可以自訂 Live Unit Testing 組建嗎？

**答：**

如果您的方案需要非「一般」非檢測組建所需的自訂步驟，以針對檢測設備 (Live Unit Testing) 進行建置，您可以將程式碼新增至專案或 .targets 檔案來檢查 `BuildingForLiveUnitTesting` 屬性，並執行自訂的建置前/後步驟。 您也可以根據這個專案屬性，選擇針對 Live Unit Testing 組建移除特定的建置步驟 (例如發佈或產生封裝)，或新增建置步驟 (例如複製必要條件)。 這並不會更改您的一般組建，而只會影響 Live Unit Testing 組建。

例如，可能有一個目標會在一般建置期間產生 NuGet 封裝。 您可能不想讓 NuGet 封裝在每次進行編輯之後產生。 因此您可以執行類似下列的內容，在 Live Unit Testing 組建中停用該目標：  

```xml
<Target Name="GenerateNuGetPackages" BeforeTargets="AfterBuild" Condition="'$(BuildingForLiveUnitTesting)' != 'true'">
    <Exec Command='"$(MSBuildThisFileDirectory)..\tools\GenPac" '/>
</Target>
```

## <a name="error-messages-with-ltoutputpathgt-or-ltoutdirgt"></a>具有 &lt;OutputPath&gt; 或 &lt;OutDir&gt; 的錯誤訊息

**為什麼我會在 Live Unit Testing 嘗試建置我的方案時，收到下列錯誤：「...似乎會無條件地設定 `<OutputPath>` 或 `<OutDir>`。Live Unit Testing 將不會從輸出組件執行測試」？**

**答：**

如果您方案的建置流程會無條件地覆寫 `<OutputPath>` 或 `<OutDir>`，使它不再是 `<BaseOutputPath>` 的子目錄，即會發生此情況。 在這種情況下，Live Unit Testing 將無法運作，因為它也會覆寫這些項目，以確保組建成品會卸除到 `<BaseOutputPath>` 下方的資料夾中。 如果您必須覆寫您想要在一般組建中卸除組建成品的位置，請根據 `<BaseOutputPath>` 有條件地覆寫 `<OutputPath>`。

例如，如果您的組建會覆寫 `<OutputPath>`，如下所示：

```xml 
<Project>
  <PropertyGroup>
    <OutputPath>$(SolutionDir)Artifacts\$(Configuration)\bin\$(MSBuildProjectName)</OutputPath>
  </PropertyGroup>
</Project>
```

則您可以使用下列程式碼來取代它：

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
 
## <a name="setting-the-location-of-live-unit-testing-build-artifacts"></a>設定 Live Unit Testing 組建成品的位置

**我想要使 Live Unit Testing 組建的成品移到特定位置，而不是 `.vs` 資料夾下方的預設位置。如何變更該位置？**

**答：**

將 `LiveUnitTesting_BuildRoot` 使用者層級環境變數設為您想要卸除 Live Unit Testing 組建成品的路徑。 

## <a name="how-is-running-tests-from-test-explorer-window-different-from-running-tests-in-live-unit-testing"></a>從 [測試總管] 視窗執行測試，與在 Live Unit Testing 中執行測試有何不同？

**答：**

差異如下：

- 從 [測試總管] 視窗針對測試進行執行或偵錯會執行一般的二進位檔，而 Live Unit Testing 會執行已檢測的二進位檔。 如果您想要偵錯已檢測的二進位檔，在您的測試方法中新增 [Debugger.Launch](xref:System.Diagnostics.Debugger.Launch) 方法呼叫會導致偵錯工具在每次執行該方法時 (包括 Live Unit Testing 執行該方法時) 啟動，您接著便可以附加已檢測的二進位檔，並對它進行偵錯。 不過，我們希望檢測設備在大部分的使用者案例中對您而言是透明的，且您不會需要對已檢測的二進位檔進行偵錯。

- Live Unit Testing 不會建立新的應用程式定義域來執行測試，但從 [測試總管] 視窗中執行的測試會建立新的應用程式定義域。

- Live Unit Testing 會循序執行每個測試組件中的測試，然而，如果您從 [測試總管] 視窗執行多個測試，並選取 [平行執行測試] 按鈕，測試將會平行執行。

- 在 Live Unit Testing 中探索和執行測試會使用 `TestPlatform` 的第 2 版，而 [測試總管] 視窗則會使用第 1 版。 儘管如此，您在大多數情況下應該不會注意到任何差異。 

- 根據預設，[測試總管] 目前會在單一執行緒 Apartment (STA) 中執行測試，而 Live Unit Testing 會在多執行緒 Apartment (MTA) 中執行測試。 若要在 Live Unit Testing 於 STA 中執行 MSTest 測試，請利用可在 `MSTest.STAExtensions 1.0.3-beta` NuGet 封裝中找到的 `<STATestMethod>` 或 `<STATestClass>` 屬性，來裝飾測試方法或包含類別。 針對 NUnit，請使用 `<RequiresThread(ApartmentState.STA)>` 屬性來裝飾測試方法，而針對 xUnit，請使用 `<STAFact>` 屬性。

## <a name="how-do-i-exclude-tests-from-participating-in-live-unit-testing"></a>如何從 Live Unit Testing 排除測試？

**答：**

請參閱[使用 Visual Studio 2017 Enterprise Edition 中的 Live Unit Testing](live-unit-testing.md#including-and-excluding-test-projects-and-test-methods) 主題中的＜包含和排除測試專案與測試方法＞一節，以了解使用者特定的設定。 若您想要針對特定的編輯工作階段執行一組特定的測試，或保存您個人的喜好設定，這非常有用。
 
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

## <a name="why-are-win32-pe-headers-different-in-instrumented-assemblies-built-by-live-unit-testing"></a>為什麼 Live Unit Testing 所建置之已檢測組件中的 Win32 PE 標頭會不一樣？

**答：**

此問題已修正，而且不存在於 Visual Studio 2017 版本 15.3 中。 請升級為這版的 Visual Studio。

在舊版 Visual Studio 2017 中，有一個已知 Bug 可能會造成 Live Unit Testing 組建無法內嵌下列 Win32 PE 標頭資料：

- 檔案版本 (在程式碼中由 @System.Reflection.AssemblyFileVersionAttribute 指定)。

- Win32 圖示 (在命令列上由 `/win32icon:` 指定)。

- Win32 資訊清單 (在命令列上由 `/win32manifest:` 指定)。

透過 Live Unit Testing 執行時，依賴這些值的測試可能會失敗。

## <a name="why-does-live-unit-testing-keep-building-my-solution-all-the-time-even-if-i-am-not-making-any-edits"></a>為什麼 Live Unit Testing 會持續建置我的方案，即使我沒有做出任何編輯也一樣？

**答：**

如果您方案的建置流程會產生屬於方案本身的原始程式碼，而您的建置目標檔案並未指定適當的輸入和輸出，即會發生此情況。 您應該為目標提供輸入和輸出清單，讓 MSBuild 可以執行適當的更新狀態檢查，並判斷是否需要新的組建。

每當 Live Unit Testing 偵測到原始程式檔已變更時，即會開始建置。 由於您方案的組建會產生原始程式檔，Live Unit Testing 將陷入無限的建置迴圈。 不過，如果在 Live Unit Testing 開始第二個組建時 (從上一個組建中偵測到新產生的原始程式檔之後) 檢查目標的輸入和輸出，它就會脫離該迴圈，因為輸入和輸出檢查將指出一切均為最新狀態。  

## <a name="how-does-live-unit-testing-work-with-the-lightweight-solution-load-feature"></a>Live Unit Testing 如何與輕量型解決方案載入功能搭配運作？

**答：**

Live Unit Testing 目前無法與輕量型解決方案載入功能良好搭配。 它只有在載入至少一個測試專案之後才會運作。 在那之前，它將不會運作，因為 Live Unit Testing 相依於至少一個參考所載入測試配接器 (MSTest、xUnit 或 NUnit) 的測試專案。

> [!NOTE]
> Visual Studio 2017 15.5 版和更新版本不再提供輕量型解決方案載入。 在 Visual Studio 2017 15.5 版和更新版本中，即便不使用輕量型解決方案載入，含有受控碼之大型解決方案的載入速度也比過去更快。

## <a name="why-does-live-unit-testing-does-not-capture-coverage-from-a-new-process-created-by-a-test"></a>為什麼 Live Unit Testing 無法從測試所建立的新流程中擷取涵蓋範圍？

**答：**

這是已知問題，應該在 Visual Studio 2017 的後續更新中修正此問題。

## <a name="why-does-nothing-happen-after-i-include-or-exclude-tests-from-the-live-test-set"></a>為什麼在我將測試包含或排除於即時測試組之後，什麼都沒有發生？

**答：**

此問題已修正，且已不存在於 Visual Studio 2017 15.3 版中。 請升級至此版本的 Visual Studio。

在舊版 Visual Studio 2017 中，這是已知問題。 此問題的因應措施為在包含或排除測試之後，對任意檔案進行編輯。 

## <a name="live-unit-testing-and-editor-icons"></a>Live Unit Testing 和編輯器圖示

**儘管根據輸出視窗中的訊息，Live Unit Testing 似乎正在執行測試，但為什麼我在編輯器中看不到任何圖示？**

**答：**

如果 Live Unit Testing 正在運作的組件基於任何原因而未進行檢測，即會發生此情況。 例如，Live Unit Testing 與設定 `<UseHostCompilerIfAvailable>false</UseHostCompilerIfAvailable>` 的專案不相容。 在此情況下，您的建置流程需要更新以移除此設定，或將該設定變更為 `true`，Live Unit Testing 才能夠運作。 

## <a name="how-do-i-collect-more-detailed-logs-to-file-bug-reports"></a>如何收集更詳細的記錄以提出錯誤報告？

**答：**

您可以執行數個動作來收集更詳細的記錄：

- 移至 [工具]，[選項]，[Live Unit Testing]，然後將記錄選項變更為 [詳細資訊]。 這會使輸出視窗顯示更詳細的記錄。

- 將 `LiveUnitTesting_BuildLog` 使用者環境變數設為您想要用來擷取 MSBuild 記錄的檔案名稱。 然後就能從該檔案中擷取來自 Live Unit Testing 組建的詳細 MSBuild 記錄訊息。

- 將 `LiveUnitTesting_TestPlatformLog` 使用者環境變數設成 `1` 以擷取測試平台記錄檔。 然後就能從該 `[Solution Root]\.vs\[Solution Name]\log\[VisualStudio Process ID]` 中擷取來自即時單元測試回合的詳細測試平台記錄訊息。

- 建立名為 `VS_UTE_DIAGNOSTICS` 的使用者層級環境變數，並將它設為 1 (或任何值)，然後重新啟動 Visual Studio。 現在您應該會在 Visual Studio 的 [輸出 - 測試] 索引標籤中看見許多記錄。

## <a name="see-also"></a>另請參閱

[即時單元測試](live-unit-testing.md)

