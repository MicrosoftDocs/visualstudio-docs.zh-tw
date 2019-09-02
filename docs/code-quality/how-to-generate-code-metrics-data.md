---
title: 從 IDE 或命令列產生程式碼計量
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe82fc213937b7e494afd27bfd964347c17e2b8
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70179988"
---
# <a name="how-to-generate-code-metrics-data"></a>HOW TO：產生程式碼度量資料

您可以用三種方式產生程式碼計量資料:

- 藉由安裝[FxCop 分析器](#fxcop-analyzers-code-metrics-rules)並啟用其包含的四個程式碼計量 (可維護性) 規則。

- 在 Visual Studio 內選擇 [ [**分析** > ] [**計算程式碼計量**](#calculate-code-metrics-menu-command) ] 功能表命令。

- 從的[命令列](#command-line-code-metrics) C#和 Visual Basic 專案。

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop 分析器程式碼計量規則

[FxCopAnalyzers NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)包含數個程式碼計量[分析器](roslyn-analyzers-overview.md)規則:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

這些規則預設為停用, 但您可以從[**方案總管**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer)或在[規則集](using-rule-sets-to-group-code-analysis-rules.md)檔案中啟用它們。 例如, 若要啟用規則 CA1502 做為警告, 則您的規則集檔案會包含下列專案:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>組態

您可以設定 FxCop 分析器封裝中的程式碼計量規則引發的臨界值。

1. 建立文字檔 例如, 您可以將它命名為*CodeMetricsConfig .txt*。

2. 以下列格式將所需的臨界值新增至文字檔:

   ```txt
   CA1502: 10
   ```

   在此範例中, 規則[CA1502](ca1502-avoid-excessive-complexity.md)設定為在方法的圈複雜度大於10時引發。

3. 在 Visual Studio 的 [**屬性**] 視窗中, 或在專案檔中, 將設定檔的 [建立] 動作標記為[**AdditionalFiles**](../ide/build-actions.md#build-action-values)。 例如：

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>計算程式碼度量功能表命令

使用 [**分析** > ] [**計算程式碼計量**] 功能表, 在 IDE 中為您的一個或所有開啟的專案產生程式碼計量。

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>產生整個解決方案的程式碼度量結果

您可以使用下列任何方式來產生整個解決方案的程式碼計量結果:

- 從功能表列中, 選擇 [**分析** > ] [計算**方案的程式** **代碼計量** > ]。

- 在**方案總管**中, 以滑鼠右鍵按一下方案, 然後選擇 [**計算程式碼度量**]。

- 在 [程式**代碼計量結果**] 視窗中, 選擇 [**計算方案的程式碼度量**] 按鈕。

系統會產生結果, 並顯示 [程式**代碼度量] 結果**視窗。 若要查看結果詳細資料, 請展開 [階層] 欄中的樹狀**結構**。

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>產生一或多個專案的程式碼度量結果

1. 在 **方案總管**中, 選取一或多個專案。

1. 從功能表列中, 選擇 [**分析** > ] [計算**所選項目的程式** **代碼計量** > ]。

系統會產生結果, 並顯示 [程式**代碼度量] 結果**視窗。 若要查看結果詳細資料, 請展開階層中的樹狀**結構**。

::: moniker range="vs-2017"

> [!NOTE]
> [**計算程式碼計量**] 命令不適用於 .net Core 和 .NET Standard 專案。 若要計算 .NET Core 或 .NET Standard 專案的程式碼計量, 您可以:
>
> - 改為從[命令列](#command-line-code-metrics)計算程式碼度量
>
> - 升級至[Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>命令列程式碼計量

您可以從命令列產生程式C#代碼計量資料, 並針對 .NET FRAMEWORK、.net Core 和 .NET Standard 應用程式 Visual Basic 專案。 若要從命令列執行程式碼計量, 請安裝[CodeAnalysis NuGet 套件](#microsoftcodeanalysismetrics-nuget-package), 或自行建立[公制](#metricsexe)可執行檔。

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>CodeAnalysis。計量 NuGet 套件

從命令列產生程式碼計量資料的最簡單方式, 就是安裝[CodeAnalysis](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet 套件。 安裝套件之後, 請從包含您`msbuild /t:Metrics`專案檔的目錄執行。 例如：

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

您可以藉由指定`/p:MetricsOutputFile=<filename>`來覆寫輸出檔案名。 您也可以藉由指定`/p:LEGACY_CODE_METRICS_MODE=true`來取得[舊版樣式的程式](#previous-versions)代碼計量資料。 例如：

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>程式碼度量輸出

產生的 XML 輸出會採用下列格式:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>計量 .exe

如果您不想要安裝 NuGet 套件, 您可以直接產生並使用*sn.exe*可執行檔。 若要產生*sn.exe*可執行檔:

1. 複製[dotnet/roslyn-分析器](https://github.com/dotnet/roslyn-analyzers)存放庫。
2. 以系統管理員身分開啟 Visual Studio 的開發人員命令提示字元。
3. 從**roslyn-分析器**存放庫的根目錄, 執行下列命令:`Restore.cmd`
4. 將目錄變更為*src\Tools*。
5. 執行下列命令來建立**計量 .csproj**專案:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   在存放庫根目錄下的*artifacts\bin*目錄中, 會產生名為 sn.exe 的可執行檔 *。*

#### <a name="metricsexe-usage"></a>計量 .exe 使用方式

若要執行*sn.exe*, 請提供專案或方案和輸出 XML 檔做為引數。 例如：

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>舊版模式

您可以選擇在*舊版模式*中建立*公制。* 此工具的舊版模式會產生[較接近舊版工具所產生](#previous-versions)的度量值。 此外, 在舊版模式中,*公制*會針對舊版工具針對所產生之程式碼計量的同一組方法類型來產生程式碼度量。 例如, 它不會產生欄位和屬性初始化運算式的程式碼計量資料。 舊版模式適用于回溯相容性, 或如果您有以程式碼計量編號為基礎的程式碼簽入閘道。 以舊版模式建立*計量*的命令為:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

如需詳細資訊, 請參閱[啟用在舊版模式中產生程式碼計量](https://github.com/dotnet/roslyn-analyzers/pull/1841)。

### <a name="previous-versions"></a>舊版本

Visual Studio 2015 包含一個也稱為「*公制*」的命令列程式碼計量工具。 這個舊版的工具進行了二進位分析, 也就是以元件為基礎的分析。 新的*計量 .exe*工具會改為分析原始程式碼。 由於新的 wsdl.exe 工具是原始程式碼型的, 因此命令列程式碼計量結果與 Visual Studio IDE 和舊版的*公制*所產生的不同。

新的命令列程式碼計量工具會在發生原始程式碼錯誤時計算計量, 只要可以載入方案和專案。

#### <a name="metric-value-differences"></a>度量值差異

在新的命令列程式碼計量工具中,度量更精確且可靠。`LinesOfCode` 它與任何 codegen 差異無關, 當工具組或執行時間變更時, 並不會變更。 新工具會計算實際的程式程式碼數, 包括空白行和留言。

其他度量 (例如`CyclomaticComplexity`和`MaintainabilityIndex` ) 會使用與先前版本的*公制*相同的公式, 但新`IOperations`的工具會計算 (邏輯來源指示) 的數目, 而不是中繼語言 (IL) 指令。 數位會與 Visual Studio IDE 和舊版的*公制*所產生的數目稍有不同。

## <a name="see-also"></a>另請參閱

- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)
- [程式碼度量值](../code-quality/code-metrics-values.md)
