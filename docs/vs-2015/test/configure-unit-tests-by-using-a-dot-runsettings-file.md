---
title: 使用 .runsettings 檔案設定單元測試 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9779dd685ad662cd0761dc85be58d0dbb3ccf0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660660"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>使用 .runsettings 檔案設定單元測試
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 *.runsettings 檔案設定 Visual Studio 中的單元測試。 (檔案名稱並不重要，但前提是您使用副檔名 '.runsettings'。) 例如，您可以變更執行測試的 .NET Framework、傳遞測試結果的所在目錄，以及測試回合期間所收集的資料。

 如果您不想要執行任何特殊組態，則不需要 *.runsettings 檔案。 最常見做法是自訂[程式碼涵蓋範圍](../test/customizing-code-coverage-analysis.md)。

> [!NOTE]
> **.runsettings 和 .testsettings**
>
> 有兩種類型的檔案可用來設定測試。 *.runsettings 是用於單元測試。 \*.Testsettings 適用于[實驗室環境測試](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)、web 效能和負載測試，以及用於自訂一些類型的診斷資料配接器，例如 IntelliTrace 和事件記錄檔介面卡。
>
> 在舊版 Visual Studio 到 2010 中，也是使用 *.testsettings 檔案來自訂單元測試。 您還是可以這麼做，但是測試的執行速度比使用 \*.runsettings 檔案中的對等組態還要慢。

## <a name="customizing-tests-with-a-runsettings-file"></a>使用 .runsettings 檔案自訂測試

1. 將 XML 檔案加入至 Visual Studio 方案，並將它重新命名為 test.runsettings。 (檔案名稱並不重要，但是副檔名必須是 .runsettings。)

2. 以 [範例](#example)取代檔案內容。

    依照您自已的需求進行編輯。

3. 在 [測試] **** 功能表中選擇 [測試設定] ****、[選取測試設定檔] ****。

   您可以在方案中建立多個 \*.runsettings 檔案，並且使用 [測試設定]**** 功能表在不同的時間將它們啟用或停用。

   ![啟用回合設定檔](../test/media/runsettings-1.png ".Runsettings-1")

## <a name="copy-this-example-runsettings-file"></a><a name="example"></a> 複製這個範例 .runsettings 檔案
 以下是一般 *.runsettings 檔案。 因為每個值都有預設值，因此該檔案的每個項目都是選擇性的。

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to solution directory -->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- [x86] | x64
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
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

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at runtime -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

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

 您也可以使用 .runsettings 檔案設定[程式碼涵蓋範圍](../test/customizing-code-coverage-analysis.md)。

 本主題的其餘部分說明檔案內容。

## <a name="edit-your-runsettings-file"></a>編輯您的 .runsettings 檔案
 .runsettings 檔案具有下列項目。

### <a name="test-run-configuration"></a>測試回合組態

|節點|預設|值|
|----------|-------------|------------|
|`ResultsDirectory`||將放置測試結果的目錄。|
|`TargetFrameworkVersion`|Framework40|Framework35、Framework40、Framework45<br /><br /> 這會指定用來尋找及執行測試的單元測試架構版本。 它可以與您在單元測試專案建置屬性中指定的 .NET 平台版本不同。|
|`TargetPlatform`|x86|x86、x64|
|`TreatTestAdapterErrorsAsWarnings`|false|false、true|
|`TestAdaptersPaths`||TestAdapter 所在目錄的一或多個路徑|
|`MaxCpuCount`|1|這會使用電腦上的可用核心，在執行單元測試時控制平行測試執行的程度。  測試執行引擎會作為每個可用核心上的不同處理序啟動，並將要執行測試的容器 (例如組件、DLL 或相關成品) 提供給每個核心。  測試容器是排程單元。  在每個容器中，會根據測試架構執行測試。  如果有許多容器，當處理序執行完容器中的測試時，就會將下一個可用的容器提供給處理序。<br /><br /> MaxCpuCount 可以是：<br /><br /> n，其中 1 <= n <= 核心數目：最多會啟動 n 個處理序<br /><br /> n，其中 n = 任何其他值：啟動的處理序數目最多可以與電腦上的可用核心數目相同|

### <a name="diagnostic-data-adapters-data-collectors"></a>診斷資料配接器 (資料收集器)
 `DataCollectors` 項目指定診斷資料配接器的設定。 診斷資料配接器用於收集有關環境與待測應用程式的其他資訊。 每個配接器都有預設設定，如果您不想要使用預設值，您只需提供設定值即可。

#### <a name="code-coverage-adapter"></a>程式碼涵蓋範圍配接器
 程式碼涵蓋範圍資料收集器會建立測試中已執行過之應用程式程式碼部分的記錄。 如需自訂程式碼涵蓋範圍設定的詳細資訊，請參閱[自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)。

#### <a name="other-diagnostic-data-adapters"></a>其他診斷資料配接器
 程式碼涵蓋範圍配接器是目前唯一可透過使用回合設定檔來自訂的配接器。

 若要自訂任何其他類型的診斷資料配接器，您必須使用測試設定檔。 如需詳細資訊，請參閱[指定 Visual Studio 測試的測試設定](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)。

#### <a name="testrunparameters"></a>TestRunParameters
 TestRunParameters 提供可供在執行階段的測試使用之定義變數和值的方式。

### <a name="mstest-run-settings"></a>MSTest 回合設定
 這些是執行具有 `[TestMethod]` 屬性之測試方法的測試配接器專屬的設定。

|組態|預設|值|
|-------------------|-------------|------------|
|ForcedLegacyMode|false|Visual Studio 2012 中的 MSTest 配接器已進行過最佳化，因此更快速且更具延展性。 某些行為 (例如測試執行順序) 可能與舊版 Visual Studio 稍有出入。 將此值設為 `true` 即可使用舊的測試配接器。<br /><br /> 例如，如果您為單元測試指定 app.config 檔案，則可以使用此方式。<br /><br /> 建議您考慮重構測試，以便使用較新的配接器。|
|IgnoreTestImpact|false|在 MSTest 或 Microsoft Test Manager 中執行時，測試影響功能會為最近變更所影響的測試設定優先權。 這項設定會停用該功能。 如需詳細資訊，請參閱[如何：收集資料以檢查程式碼變更後應該要執行的測試](https://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47)。|
|SettingsFile||您可以指定與此處的 MS 測試配接器一起使用的測試設定檔。 您也可以使用 [測試] **** 功能表、[測試設定] ****、[選取測試設定檔] **** 來指定測試設定檔。<br /><br /> 如果您指定這個值，也必須將 [ **ForcedlegacyMode** ] 設定為 [ **true**]。<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|
|KeepExecutorAliveAfterLegacyRun|false|測試回合完成後，會關閉 MSTest。 此時也會終止所有在測試過程中啟動的處理序。 如果您想要讓測試執行程式保持運作，請將這個組態設為 true。<br /><br /> 例如，您可以使用此方式讓瀏覽器在不同的自動程式碼 UI 測試之間保持執行。|
|DeploymentEnabled|true|如果將此設定為 false，就不會將您在測試方法中指定的部署項目複製到部署目錄中。|
|CaptureTraceOutput|true|您可以使用 Trace.WriteLine 從測試方法寫入偵錯追蹤。 使用此組態可以關閉這些偵錯追蹤。|
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|您可以將此值設定為 false，在測試回合之後保留部署目錄。|
|MapInconclusiveToFailed|false|如果測試傳回結果不明狀態，通常與測試總管中的 [已略過] 狀態對應。 如果您要將結果不明的測試顯示為 [失敗]，請使用這種組態。|
|InProcMode|false|如果您想要在 MS 測試配接器的處理序中執行測試，請將此值設定為 true。 這個設定提供較小效能。 但如果測試因為例外狀況而結束，其他測試將不會繼續。|
|AssemblyResolution|false|您可以在求解及執行單元測試時，指定其他組件的路徑。  例如，您可以針對與測試組件位於不同目錄的相依性組件，使用這些路徑。  若要指定路徑，請使用 "Directory Path" 項目。  路徑可以包含環境變數。<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>另請參閱
 [自訂程式碼涵蓋範圍分析](../test/customizing-code-coverage-analysis.md)[指定 Visual Studio 測試的測試設定](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
