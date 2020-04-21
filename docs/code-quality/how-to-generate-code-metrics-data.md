---
title: 從 IDE 或指令列產生代碼指標
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649298"
---
# <a name="how-to-generate-code-metrics-data"></a>如何:產生代碼指標資料

您可以透過三種方式產生代碼指標資料:

- 通過安裝[FxCop分析器](#fxcop-analyzers-code-metrics-rules)並啟用它包含的四個代碼指標(可維護性)規則。

- 通過在可視化工作室中選擇「[**分析** > 計算代碼指標」](#calculate-code-metrics-menu-command)功能表命令。

- 從 C# 與視覺化基本項目[的命令列](#command-line-code-metrics)。

## <a name="fxcop-analyzers-code-metrics-rules"></a>FxCop 分析器代碼指標規則

[FxCopAnalyzers NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)包括多個代碼指標[分析器](roslyn-analyzers-overview.md)規則:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

默認情況下禁用這些規則,但可以從[**解決方案資源管理員**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer)或[規則集](using-rule-sets-to-group-code-analysis-rules.md)檔中啟用這些規則。 例如,要啟用規則 CA1502 作為警告,您的 .ruleset 檔將包含以下條目:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>設定

您可以配置 FxCop 分析器包中代碼指標規則觸發的閾值。

1. 建立文字檔 例如,您可以將將*CodeMetricsConfig.txt*。

2. 以以下格式加入文字檔的限制值:

   ```txt
   CA1502: 10
   ```

   在此示例中,規則[CA1502](ca1502.md)配置為在方法的循環複雜性大於 10 時觸發。

3. 在 Visual Studio**的「屬性」** 視窗中或專案檔中,將設定檔的生成操作標記為[**「附加檔**](../ide/build-actions.md#build-action-values)」 。 例如：

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>計算代碼指標選單指令

通過使用 **「分析** > **計算代碼指標」** 功能表,為 IDE 中的一個或所有打開的專案生成代碼指標。

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>為整個解決方案產生程式碼指標結果

您可以透過以下任何方式為整個解決方案產生代碼指標結果:

- 在功能表列中,選擇 **「分析** > **計算解決方案****的代碼指標** > 」。

- 在**解決方案資源管理器**中,右鍵單擊解決方案,然後選擇 **「計算代碼指標**」。

- 在 **「代碼指標結果」** 視窗中,選擇 **「計算解決方案的代碼指標」** 按鈕。

生成結果並顯示 **「代碼指標結果**」視窗。 要查看結果詳細資訊,請展開 **「層次結構**」列中的樹。

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>為一個或多個項目產生代碼指標結果

1. 在**解決方案資源管理員中**,選擇一個或多個專案。

1. 從選單欄中,選擇 **「分析** > **計算** > **選取項目**的代碼指標」。

生成結果並顯示 **「代碼指標結果**」視窗。 要查看結果詳細資訊,請展開**層次結構**中的樹。

::: moniker range="vs-2017"

> [!NOTE]
> **計算代碼指標命令**不適用於 .NET Core 和 .NET 標準專案。 要計算 .NET Core 或 .NET 標準項目的代碼指標,可以:
>
> - 而是從[命令列](#command-line-code-metrics)計算代碼指標
>
> - 升級到[視覺工作室 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>命令列代碼指標

可以從 .NET Framework、.NET Core 和 .NET 標準應用的 C# 和 Visual Basic 專案的命令行生成代碼指標數據。 要從命令列運行代碼指標,請安裝[Microsoft.CodeAnalysis.Metrics NuGet 包](#microsoftcodeanalysismetrics-nuget-package)或自行構建[指標.exe](#metricsexe)可執行檔。

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>微軟.程式碼分析.指標 NuGet 套件

從命令列生成代碼指標數據的最簡單方法是安裝[Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet 包。 安裝包後,從包含專案檔的目錄`msbuild /t:Metrics`運行。 例如：

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

可以通過`/p:MetricsOutputFile=<filename>`指定 覆蓋輸出檔名來覆蓋輸出檔名。 還可以通過指定`/p:LEGACY_CODE_METRICS_MODE=true`獲取[舊式](#previous-versions)代碼指標數據。 例如：

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

### <a name="code-metrics-output"></a>代碼指標輸出

產生的 XML 輸出以以下格式:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>指標.exe

如果不想安裝 NuGet 包,可以直接生成和使用*Metrics.exe*可執行檔。 要產生*指標.exe*執行檔:

1. 克隆[點網/羅斯林分析器](https://github.com/dotnet/roslyn-analyzers)回購。
2. 打開 Visual Studio 的開發人員命令提示符作為管理員。
3. 從**roslyn 分析器**回購的根,執行以下命令:`Restore.cmd`
4. 將目錄變更為*src_Tools*。
5. 執行以下指令以產生**Metrics.csproj**專案:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   在儲存庫根目錄下*的專案\bin*目錄中生成名為*Metrics.exe*的可執行檔。

#### <a name="metricsexe-usage"></a>指標.exe 用法

要運行*Metrics.exe,* 提供專案或解決方案以及輸出 XML 檔案作為參數。 例如：

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>舊模式

您可以選擇在*舊模式下*建構*指標.exe。* 該工具的舊模式版本生成的指標值更接近[工具的舊版本](#previous-versions)生成。 此外,在舊模式下 *,Metrics.exe*為工具的早期版本為其生成代碼指標的相同方法類型生成代碼指標。 例如,它不為欄位和屬性初始化器生成代碼指標數據。 舊版模式對於向後相容性或基於代碼指標編號的代碼簽入門非常有用。 在舊模式下產生*Metrics.exe*的指令是:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

有關詳細資訊,請參閱[在舊模式下啟用產生代碼指標](https://github.com/dotnet/roslyn-analyzers/pull/1841)。

### <a name="previous-versions"></a>舊版

::: moniker range=">=vs-2019"
Visual Studio 2015 包含指令列代碼指標工具,也稱為*Metrics.exe*。 該工具的早期版本做了二進制分析,即基於程式集的分析。 較新版本的*Metrics.exe*工具將分析原始程式碼。 由於較新的*Metrics.exe*工具基於原始碼,因此命令列代碼指標的結果可能與 Visual Studio IDE 和早期*版本的 Metrics.exe*生成的指標不同。 從 Visual Studio 2019 開始,Visual Studio IDE 會分析原始程式碼,如命令列工具,結果應相同。

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 包含指令列代碼指標工具,也稱為*Metrics.exe*。 該工具的早期版本做了二進制分析,即基於程式集的分析。 新的*Metrics.exe*工具將分析原始碼。 由於新的*Metrics.exe*工具基於原始碼,因此命令列代碼指標結果與 Visual Studio IDE 和早期*版本的 Metrics.exe*生成的結果不同。
::: moniker-end

新的命令列代碼指標工具即使在存在原始程式碼錯誤的情況下也計算指標,只要可以載入解決方案和專案。

#### <a name="metric-value-differences"></a>指標值差異

::: moniker range=">=vs-2019"
從 Visual Studio 2019 版本 16.4 和 Microsoft.CodeAnalysis.Metics `SourceLines` (2.9.5) 開始,並`ExecutableLines`替換以前的`LinesOfCode`指標。 有關新指標的說明,請參閱[程式碼指標值](../code-quality/code-metrics-values.md)。 該`LinesOfCode`指標在舊模式下可用。
::: moniker-end
::: moniker range="vs-2017"
在新的`LinesOfCode`命令列代碼指標工具中,該指標更準確、更可靠。 它獨立於任何代碼項差異,並且在工具集或運行時更改時不會更改。 新工具計算實際代碼行,包括空白行和註釋。
::: moniker-end

其他`CyclomaticComplexity`指標(如和`MaintainabilityIndex`使用的公式與以前版本的*Metrics.exe)* 相同,但新工具計算(`IOperations`邏輯來源 指令)的數量,而不是中間語言 (IL) 指令的數量。 這些數位將略有不同,由視覺工作室IDE和早期版本的*Metrics.exe*生成。

## <a name="see-also"></a>另請參閱

- [使用「代碼指標結果」 視窗](../code-quality/working-with-code-metrics-data.md)
- [代碼指標值](../code-quality/code-metrics-values.md)
