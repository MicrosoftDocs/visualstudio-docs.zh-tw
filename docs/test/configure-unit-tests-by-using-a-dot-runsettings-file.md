---
title: 使用 .runsettings 檔案設定單元測試
description: 瞭解如何在 Visual Studio 中使用 .runsettings 檔案，以設定從命令列、從 IDE 或在組建工作流程中執行的單元測試。
ms.custom: SEO-VS-2020
ms.date: 07/15/2020
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: ff92d7c53b2b7e5f5c89fbc37226135d5331acbb
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2021
ms.locfileid: "103295771"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>使用 *.runsettings* 檔案設定單元測試

您可以使用 *.runsettings* 檔案來設定 Visual Studio 中的單元測試。 例如，您可以變更執行測試的 .NET 版本、測試結果的所在目錄，或在測試回合期間所收集的資料。 *.runsettings* 檔案常見的用法是用來自訂 [程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

您可以使用回合設定檔案來設定從 [命令列](vstest-console-options.md)、IDE，或使用 Azure 測試計劃或 Team Foundation SERVER (TFS) 在 [組建工作流程](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true) 中執行的測試。

回合設定檔為選擇性。 如果您不需要任何特殊設定，就不需要 *.runsettings* 檔案。

## <a name="create-a-run-settings-file-and-customize-it"></a>建立執行設定檔並加以自訂

1. 將回合設定檔新增至方案。 在 [**方案瀏覽器**] 中，于方案的快捷方式功能表上，選擇 [**加入**  >  **新專案**]，然後選取 [ **XML** 檔案]。 使用 *.runsettings* 之類的名稱來儲存檔案。

   > [!TIP]
   > 檔案名稱並不重要，只要使用的副檔名為 .runsettings 即可。

2. 從 [範例 *. .runsettings](#example-runsettings-file)檔案新增內容，然後根據您的需求進行自訂，如下列各節所述。

3. 使用下列其中一種方法，指定您想要的 *. .runsettings 檔案：

   - [Visual Studio IDE](#specify-a-run-settings-file-in-the-ide)
   - [命令列](#specify-a-run-settings-file-from-the-command-line)
   - 使用 Azure 測試計劃或 Team Foundation Server (TFS) 來[建立工作流程](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)。

4. 執行單元測試，以使用自訂回合設定。

::: moniker range="vs-2017"

如果您想要在 IDE 中關閉和開啟自訂設定，請取消選取或選取 [ **測試** > **測試設定** ] 功能表中的檔案。

![Visual Studio 2017 中具有自訂設定檔的測試設定功能表](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

如果您想要在 IDE 中關閉和開啟自訂設定，請取消選取或選取 [ **測試** ] 功能表上的檔案。

::: moniker-end

> [!TIP]
> 您可以在方案中建立多個 .runsettings 檔案，然後視需要選取其中一個作為使用中測試設定檔。

## <a name="specify-a-run-settings-file-in-the-ide"></a>在 IDE 中指定回合設定檔

可用的方法取決於您的 Visual Studio 版本。

::: moniker range="vs-2017"
若要在 IDE 中指定回合設定檔，請選取 [測試]**[測試設定]** > **[選取測試設定檔]** > ，然後選取 *.runsettings* 檔案。

![在 Visual Studio 2017 中選取測試設定檔的功能表](media/select-test-settings-file.png)

檔案隨即出現在 [測試設定] 功能表中，且您可以選取或取消選取它。 選取時，只要選取 [分析程式碼涵蓋範圍]，就會套用回合設定檔。
::: moniker-end

::: moniker range=">=vs-2019"

### <a name="visual-studio-2019-version-164-and-later"></a>Visual Studio 2019 16.4 版和更新版本

有三種方式可在 Visual Studio 2019 16.4 版和更新版本中指定回合設定檔案。

- [自動偵測回合設定](#autodetect-the-run-settings-file)
- [手動設定回合設定](#manually-select-the-run-settings-file)
- [設定組建屬性](#set-a-build-property)

#### <a name="autodetect-the-run-settings-file"></a>自動偵測回合設定檔

> [!NOTE]
> 這只適用于名為的檔案 `.runsettings` 。

若要自動偵測回合設定檔，請將它放在解決方案的根目錄中。

如果啟用回合設定檔案的自動偵測功能，則會在所有測試回合上套用此檔案中的設定。 您可以使用兩種方法開啟自動偵測 .runsettings 檔案：

- 選取 **工具** > **選項** > **測試** > **自動偵測 .runsettings** 檔案

   ![Visual Studio 2019 中的自動偵測 .runsettings 檔案選項](media/vs-2019/auto-detect-runsettings-tools-window.png)

- 選取 **測試** 設定回合 > **設定** > **自動偵測 .runsettings** 檔案

   ![Visual Studio 2019 中的自動偵測 .runsettings 檔案功能表](media/vs-2019/auto-detect-runsettings-menu.png)

#### <a name="manually-select-the-run-settings-file"></a>以手動方式選取回合設定檔案

在 IDE 中，選取 [ **測試** 設定回合 > **設定**] > **選取 [方案範圍 .runsettings** 檔]，然後選取 *.runsettings* 檔案。

   - 這個檔案會覆寫位於方案根目錄的 *.runsettings* 檔案（如果有的話），並套用到所有測試回合。
   - 此檔案選取專案只會在本機保存。

![選取 Visual Studio 2019 中的測試全解決方案 .runsettings 檔功能表](media/vs-2019/select-solution-settings-file.png)

#### <a name="set-a-build-property"></a>設定組建屬性

透過專案檔或 .props 檔案，將組建屬性加入至專案。 專案的回合設定檔是由屬性 **RunSettingsFilePath** 所指定。

- C #、VB、c + + 和 F # 專案中目前支援專案層級的執行設定。
- 為專案指定的檔案會覆寫解決方案中指定的任何其他回合設定檔案。
- [這些 MSBuild 屬性](../msbuild/msbuild-reserved-and-well-known-properties.md) 可以用來指定 .runsettings 檔的路徑。

為專案指定 *.runsettings* 檔案的範例：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RunSettingsFilePath>$(MSBuildProjectDirectory)\example.runsettings</RunSettingsFilePath>
  </PropertyGroup>
  ...
</Project>
```

### <a name="visual-studio-2019-version-163-and-earlier"></a>Visual Studio 2019 16.3 版及更早版本

若要在 IDE 中指定回合設定檔案，請選取 [**測試**  >  **選取設定檔**]。 瀏覽並選取 *.runsettings* 檔案。

![在 Visual Studio 2019 中選取測試設定檔的功能表](media/vs-2019/select-settings-file.png)

檔案會出現在 [測試] 功能表中，您可以選取或取消選取它。 選取時，只要選取 [分析程式碼涵蓋範圍]，就會套用回合設定檔。
::: moniker-end

## <a name="specify-a-run-settings-file-from-the-command-line"></a>從命令列指定回合設定檔案

若要從命令列執行測試，請使用 *vstest.console.exe*，並使用 **/settings** 參數指定設定檔案。

1. 開啟 [Visual Studio 的開發人員命令提示](../ide/reference/command-prompt-powershell.md)字元。

2. 輸入與下列類似的命令：

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   或

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

如需詳細資訊，請參閱 [VSTest.Console.exe 命令列選項](vstest-console-options.md)。

## <a name="the-runsettings-file"></a>*. .Runsettings 檔案

*. .Runsettings 檔案是 XML 檔案，其中包含 **.runsettings** 元素內的不同設定元素。 接下來的各節會詳細說明不同的元素。 如需完整範例，請參閱 [範例 * .runsettings](#example-runsettings-file)檔案。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- configuration elements -->
</RunSettings>
```

每個設定元素都是選擇性的，因為它有預設值。

## <a name="runconfiguration-element"></a>RunConfiguration 元素

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
</RunConfiguration>
```

**RunConfiguration** 項目可以包括下列項目：

|節點|預設|值|
|-|-|-|
|**MaxCpuCount**|1|此設定會使用電腦上的可用核心，在執行單元測試時控制平行測試執行的程度。 測試執行引擎會在各個可用核心上作為不同的處理序啟動，並將要執行測試的容器提供給每個核心。 容器可以是組件、DLL 或相關成品。 測試容器是排程單元。 在每個容器中，會根據測試架構執行測試。 如果有許多容器，當處理序執行完容器中的測試時，就會將下一個可用的容器提供給處理序。<br /><br />MaxCpuCount 可以是：<br /><br />n，其中 1 <= n <= 核心數目：最多會啟動 n 個處理序<br /><br />n，其中 n = 任何其他值：啟動的進程數目最多可達可用核心數目。 例如，設定 n = 0 可讓平臺根據環境自動決定要啟動的最佳進程數目。|
|**ResultsDirectory**||放置測試結果的目錄。 路徑是相對於包含 .runsettings 檔案的目錄。|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` 適用於 .NET Core 來源、`FrameworkUap10` 適用於 UWP 型來源、`Framework45` 適用於 .NET Framework 4.5 和更新版本、`Framework40` 適用於 .NET Framework 4.0，而 `Framework35` 則適用於 .NET Framework 3.5。<br /><br />此設定會指定用來尋找及執行測試的單元測試架構版本。 它可以與您在單元測試專案建置屬性中指定的 .NET 平台版本不同。<br /><br />如果您從 *.runsettings* 檔案省略 `TargetFrameworkVersion` 元素，平台會根據組建二進位檔自動判斷架構版本。|
|**TargetPlatform**|x86|x86、x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false、true|
|**TestAdaptersPaths**||TestAdapters 所在目錄的一或多個路徑|
|**TestSessionTimeout**||當測試工作階段超過指定的逾時之時，允許使用者終止測試工作階段。 設定逾時可確保資源能被充分取用，且可將測試工作階段限制在設定的時間內。 **Visual Studio 2017 15.5** 版和更新版本提供這項設定。|
|**DotnetHostPath**||指定用來執行 testhost 之 dotnet 主機的自訂路徑。 當您建立自己的 dotnet 時（例如，在建立 dotnet/執行時間存放庫時），這會很有用。 指定此選項會略過尋找 testhost.exe，且一律會使用 testhost.dll。|
|**TreatNoTestsAsError**|false| true 或 false <br>指定布林值，此值會定義未探索到任何測試時的結束代碼。 如果值為 `true` 且未探索到任何測試，則會傳回非零的結束代碼。 否則會傳回零。|

## <a name="datacollectors-element-diagnostic-data-adapters"></a>DataCollectors 元素 (診斷資料配接器) 

**DataCollectors** 項目指定診斷資料配接器的設定。 診斷資料配接器會收集有關環境與待測應用程式的其他資訊。 每個配接器都有預設設定，如果您不想要使用預設值，您只需提供設定值即可。

```xml
<DataCollectionRunSettings>
  <DataCollectors>
    <!-- data collectors -->
  </DataCollectors>
</DataCollectionRunSettings>
```

### <a name="codecoverage-data-collector"></a>CodeCoverage 資料收集器

程式碼涵蓋範圍資料收集器會建立測試中已執行過之應用程式程式碼部分的記錄。 如需自訂程式碼涵蓋範圍設定的詳細資訊，請參閱 [自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

```xml
<DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
  <Configuration>
    <CodeCoverage>
      <ModulePaths>
        <Exclude>
          <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
      </ModulePaths>

      <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
      <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
      <CollectFromChildProcesses>True</CollectFromChildProcesses>
      <CollectAspDotNet>False</CollectAspDotNet>
    </CodeCoverage>
  </Configuration>
</DataCollector>
```

### <a name="videorecorder-data-collector"></a>VideoRecorder 資料收集器

測試執行時，視訊資料收集器會擷取螢幕錄製。 這份錄製可用於 UI 測試的疑難排解。 視訊資料收集器在 **Visual Studio 2017 15.5 版** 和更新版本中提供。 如需設定此資料收集器的範例，請參閱 [範例 *. .runsettings](#example-runsettings-file)檔案。

若要自訂任何其他類型的診斷資料配接器，請使用[測試設定檔](../test/collect-diagnostic-information-using-test-settings.md)。

### <a name="blame-data-collector"></a>現象資料收集器

這個選項可協助您找出導致測試主機損毀的有問題的測試。 執行收集器會在 *TestResults* 中建立輸出檔 (*Sequence.xml*) ，以在損毀之前捕捉測試的執行順序。

```xml
<DataCollector friendlyName="blame" enabled="True">
</DataCollector>
```

## <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="docsUrl" value="https://docs.microsoft.com" />
</TestRunParameters>
```

測試回合參數提供一種方法，可定義在執行時間可供測試使用的變數和值。 使用 MSTest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType> 屬性 (或 NUnit [TestCoNtext](https://docs.nunit.org/articles/nunit/writing-tests/TestContext.html)) 來存取參數：

```csharp
private string _appUrl;
public TestContext TestContext { get; set; }

[TestMethod] // [Test] for NUnit
public void HomePageTest()
{
    string _appURL = TestContext.Properties["webAppUrl"];
}
```

若要使用測試回合參數，請 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> 在您的測試類別中加入公用屬性。

## <a name="loggerrunsettings-element"></a>LoggerRunSettings 元素

`LoggerRunSettings`區段會定義要用於測試回合的一或多個記錄器。 最常見的記錄器為主控台、Visual Studio 測試結果檔案 (.trx) 和 html。

```xml
<LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
    </Loggers>
  </LoggerRunSettings>
```

## <a name="mstest-element"></a>MSTest 元素

這些是執行具有 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性之測試方法的測試配接器專屬的設定。

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

|組態|預設|值|
|-|-|-|
|**ForcedLegacyMode**|false|Visual Studio 2012 中的 MSTest 配接器已進行過最佳化，因此更快速且更具延展性。 某些行為 (例如測試執行順序) 可能與舊版 Visual Studio 稍有出入。 將此值設定為 **true**，以使用較舊的測試配接器。<br /><br />例如，如果您為單元測試指定 *app.config* 檔案，則可以使用此設定。<br /><br />建議您考慮重構測試，以便使用較新的配接器。|
|**IgnoreTestImpact**|false|「測試影響」功能會將受最新變更影響的測試排定優先順序、在 MSTest 或 Microsoft Test Manager 中執行時 (已在 Visual Studio 2017) 中淘汰。 這項設定會停用該功能。 如需詳細資訊，請參閱[自從上次建置以來應該要執行哪些測試？](/previous-versions/dd286589(v=vs.140))。|
|**SettingsFile**||您可以指定與此處的 MS 測試配接器一起使用的測試設定檔。 您也可以[從設定功能表](#specify-a-run-settings-file-in-the-ide)指定測試設定檔。<br /><br />如果您指定這個值，也必須將 [ **ForcedlegacyMode** ] 設定為 [ **true**]。<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|測試回合完成後，會關閉 MSTest。 所有在測試過程中啟動的處理序也都會終止。 如果您要讓測試執行程式保持運作，請將此值設定為 **true**。 例如，您可以使用此設定讓瀏覽器在不同的自動程式碼 UI 測試之間保持執行。|
|**DeploymentEnabled**|true|如果您將此值設定為 **false**，就不會將您在測試方法中指定的部署項目複製到部署目錄中。|
|**CaptureTraceOutput**|true|您可以使用 <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType> 從測試方法寫入偵錯追蹤。|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|若要在測試回合之後保留部署目錄，請將此值設定為 **false**。|
|**MapInconclusiveToFailed**|false|如果測試完成，但狀態結果不明，則通常對應至 [測試總管] 中的已略過狀態。 如果您要讓結果不明的測試顯示為 [失敗]，請將此值設定為 **true**。|
|**InProcMode**|false|如果您要在 MSTest 配接器的相同處理序中執行測試，請將此值設定為 **true**。 這個設定提供較小效能。 但如果測試因例外狀況而結束，則不會執行其餘測試。|
|**AssemblyResolution**|false|您可以在求解及執行單元測試時，指定其他組件的路徑。 例如，您可以針對與測試組件位於不同目錄的相依性組件，使用這些路徑。 若要指定路徑，請使用 **目錄路徑** 項目。 路徑可以包括環境變數。<br /><br />`<AssemblyResolution>  <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="example-runsettings-file"></a>*.Runsettings* 檔案範例

下列 XML 顯示一般 .runsettings 檔案的內容。 複製此程式碼，並根據需求編輯。

檔案的每個項目都有預設值，因此為選擇性。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the Test menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>

    <!-- true or false -->
    <!-- Value that specifies the exit code when no tests are discovered -->
    <TreatNoTestsAsError>true</TreatNoTestsAsError>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
          <!-- Set "sendRecordedMediaForPassedTestCase" to "false" to add video attachments to failed tests only -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true"  xmlns="">           
            <ScreenCaptureVideo bitRate="512" frameRate="2" quality="20" />
          </MediaRecorder>
        </Configuration>
      </DataCollector>

      <!-- Configuration for blame data collector -->
      <DataCollector friendlyName="blame" enabled="True">
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Configuration for loggers -->
  <LoggerRunSettings>
    <Loggers>
      <Logger friendlyName="console" enabled="True">
        <Configuration>
            <Verbosity>quiet</Verbosity>
        </Configuration>
      </Logger>
      <Logger friendlyName="trx" enabled="True">
        <Configuration>
          <LogFileName>foo.trx</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="html" enabled="True">
        <Configuration>
          <LogFileName>foo.html</LogFileName>
        </Configuration>
      </Logger>
      <Logger friendlyName="blame" enabled="True" />
    </Loggers>
  </LoggerRunSettings>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="specify-environment-variables-in-the-runsettings-file"></a>在 *.runsettings* 檔案中指定環境變數

您可以在 *.runsettings* 檔案中設定環境變數，以便直接與測試主機互動。 需要在 *.runsettings* 檔案中指定環境變數，才能支援需要設定環境變數（例如 *DOTNET_ROOT*）的重要專案。 這些變數會在產生測試主機進程時設定，並可在主機中使用。

### <a name="example"></a>範例

下列程式碼是傳遞環境變數的 *.runsettings* 檔案：

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <RunConfiguration>
    <EnvironmentVariables>
      <!-- List of environment variables we want to set-->
      <DOTNET_ROOT>C:\ProgramFiles\dotnet</DOTNET_ROOT>
      <SDK_PATH>C:\Codebase\Sdk</SDK_PATH>
    </EnvironmentVariables>
  </RunConfiguration>
</RunSettings>
```

**RunConfiguration** 節點應包含 **EnvironmentVariables** 節點。 您可以將環境變數指定為專案名稱和其值。

> [!NOTE]
> 因為這些環境變數應該一律在測試主機啟動時設定，所以測試應該一律在個別的進程中執行。 如此一來，當有環境變數時，就會設定 */InIsolation* 旗標，讓測試主機一律會被叫用。

## <a name="see-also"></a>另請參閱

- [設定測試回合](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md) \(英文\)
- [自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)
- [Visual Studio 測試工作 (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts&preserve-view=true)
