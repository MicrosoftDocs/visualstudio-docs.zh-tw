---
title: 從 IDE 或命令列產生程式碼度量
ms.date: 11/02/2018
description: 瞭解如何在 Visual Studio 中產生程式碼度量資料。 請參閱如何使用方案總管、規則集檔案、命令列或功能表命令。
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631ce51df5d985e02e8ccabca258c0ef1c1318f4
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069470"
---
# <a name="how-to-generate-code-metrics-data"></a>How to：產生程式碼度量資料

您可以用三種方式產生程式碼計量資料：

- 藉由啟用 [.net 程式碼品質分析器](#net-code-quality-analyzers-code-metrics-rules) 並啟用四個程式碼度量， (可維護性) 其所包含的規則。

- 選擇 Visual Studio 內的 [ [**分析**  >  **計算程式碼度量**](#calculate-code-metrics-menu-command) ] 功能表命令。

- 從 c # 和 Visual Basic 專案的 [命令列](#command-line-code-metrics) 。

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>.NET 程式碼品質分析器程式碼計量規則

.NET 程式碼品質分析器包含數個程式碼計量 [分析器](roslyn-analyzers-overview.md) 規則：

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

這些規則預設為停用，但您可以從 [**方案總管**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) 或 [EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) 檔案中加以啟用。 例如，若要以警告的形式啟用規則 CA1502，您的 EditorConfig 檔會包含下列專案：

```cs
dotnet_diagnostic.CA1502.severity = warning
```

### <a name="configuration"></a>設定

您可以設定程式碼計量規則引發的臨界值。

1. 建立文字檔 例如，您可以將它命名為 *CodeMetricsConfig.txt*。

2. 以下列格式將所需的臨界值新增至文字檔：

   ```txt
   CA1502: 10
   ```

   在此範例中，規則 [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) 是設定為在方法的圈複雜度大於10時引發。

3. 在 Visual Studio 的 [ **屬性** ] 視窗中，或在專案檔中，將設定檔的組建動作標示為 [**AdditionalFiles**](../ide/build-actions.md#build-action-values)。 例如：

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>計算程式碼度量功能表命令

使用 [**分析**  >  **計算程式碼度量**] 功能表，為 IDE 中的一個或所有開啟的專案產生程式碼度量。

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>產生整個解決方案的程式碼度量結果

您可以使用下列任何一種方式產生整個解決方案的程式碼度量結果：

- 從功能表列中，選取 [**分析**  >  **計算**  >  **方案的程式** 代碼度量]。

- 在 **方案總管** 中，以滑鼠右鍵按一下方案，然後選取 [ **計算程式碼度量**]。

- 在 [程式 **代碼計量結果** ] 視窗中，選取 [ **計算方案的程式碼度量** ] 按鈕。

結果會產生並顯示 [程式 **代碼度量結果** ] 視窗。 若要查看結果詳細資料，請展開 [階層] 資料行中的樹狀 **結構** 。

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>產生一或多個專案的程式碼度量結果

1. 在 **方案總管** 中，選取一或多個專案。

1. 從功能表列中，選取 [**分析**  >  **計算**  >  **所選取專案的程式** 代碼度量])  (。

結果會產生並顯示 [程式 **代碼度量結果** ] 視窗。 若要查看結果詳細資料，請展開階層中的樹狀 **結構**。

::: moniker range="vs-2017"

> [!NOTE]
> [ **計算程式碼度量** ] 命令不適用於 .net Core 和 .NET Standard 專案。 若要計算 .NET Core 或 .NET Standard 專案的程式碼計量，您可以：
>
> - 改為從 [命令列](#command-line-code-metrics) 計算程式碼度量
>
> - 升級至 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>命令列程式碼計量

您可以從命令列針對適用于 .NET Framework、.NET Core 和 .NET Standard 應用程式的 c # 和 Visual Basic 專案產生程式碼度量資料。 若要從命令列執行程式碼計量，請安裝 [CodeAnalysis NuGet 套件](#microsoftcodeanalysismetrics-nuget-package) ，或自行建立 [Metrics.exe](#metricsexe) 可執行檔。

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>CodeAnalysis 計量 NuGet 套件

從命令列產生程式碼計量資料的最簡單方式，就是安裝 [CodeAnalysis](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet 套件。 安裝套件之後，請 `msbuild /t:Metrics` 從包含專案檔的目錄執行。 例如：

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

您可以藉由指定來覆寫輸出檔名稱 `/p:MetricsOutputFile=<filename>` 。 您也可以藉由指定來取得 [舊版樣式的程式](#previous-versions) 代碼計量資料 `/p:LEGACY_CODE_METRICS_MODE=true` 。 例如：

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

### <a name="code-metrics-output"></a>程式碼計量輸出

產生的 XML 輸出會採用下列格式：

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

### <a name="metricsexe"></a>Metrics.exe

如果您不想要安裝 NuGet 套件，可以直接產生和使用 *Metrics.exe* 可執行檔。 若要產生 *Metrics.exe* 可執行檔：

1. 複製 [dotnet/roslyn-分析器](https://github.com/dotnet/roslyn-analyzers) 存放庫。
2. 以系統管理員身分開啟 Visual Studio 的開發人員命令提示字元。
3. 從 **roslyn 分析器** 存放庫的根目錄中，執行下列命令： `Restore.cmd`
4. 將目錄變更為 *src\Tools*。
5. 執行下列命令以建立 **計量 .csproj** 專案：

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   名為 *Metrics.exe* 的可執行檔會在存放庫根目錄底下的 *artifacts\bin* 目錄中產生。

#### <a name="metricsexe-usage"></a>Metrics.exe 使用方式

若要執行 *Metrics.exe*，請提供專案或方案和輸出 XML 檔案做為引數。 例如：

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>舊版模式

您可以選擇以 *舊版模式* 建立 *Metrics.exe* 。 此工具的舊版模式會產生更接近 [所產生之舊版工具](#previous-versions)的度量值。 此外，在舊版模式中， *Metrics.exe* 會針對舊版工具產生之程式碼度量的相同一組方法類型，產生程式碼度量。 例如，它不會產生欄位和屬性初始化運算式的程式碼計量資料。 舊版模式適用于回溯相容性，或者，如果您有根據程式碼計量編號的程式碼簽入管制。 以舊版模式建立 *Metrics.exe* 的命令為：

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

如需詳細資訊，請參閱 [啟用在舊版模式中產生程式碼度量](https://github.com/dotnet/roslyn-analyzers/pull/1841)。

### <a name="previous-versions"></a>舊版

::: moniker range=">=vs-2019"
Visual Studio 2015 包含的命令列程式碼度量工具也稱為 *Metrics.exe*。 這個舊版的工具會進行二進位分析，也就是以元件為基礎的分析。 較新版本的 *Metrics.exe* 工具會改為分析原始程式碼。 因為較新的 *Metrics.exe* 工具是以程式碼為基礎，所以命令列程式碼度量結果可能與 Visual Studio IDE 和舊版 *Metrics.exe* 所產生的不同。 從 Visual Studio 2019 開始，Visual Studio IDE 會分析原始程式碼（例如命令列工具），且結果應該相同。

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 包含的命令列程式碼度量工具也稱為 *Metrics.exe*。 這個舊版的工具會進行二進位分析，也就是以元件為基礎的分析。 新的 *Metrics.exe* 工具會改為分析原始程式碼。 因為新的 *Metrics.exe* 工具是以程式碼為基礎，所以命令列程式碼度量結果與 Visual Studio IDE 和舊版 *Metrics.exe* 所產生的不同。
::: moniker-end

只要方案和專案可以載入，新的命令列程式碼度量工具就會計算計量（即使存在原始程式碼錯誤）。

#### <a name="metric-value-differences"></a>度量值差異

::: moniker range=">=vs-2019"
從 Visual Studio 2019 16.4 版和 CodeAnalysis. 計量 (2.9.5) ， `SourceLines` 並 `ExecutableLines` 取代先前的 `LinesOfCode` 度量。 如需新計量的說明，請參閱程式 [代碼度量值](../code-quality/code-metrics-values.md)。 `LinesOfCode`度量可在舊版模式中使用。
::: moniker-end
::: moniker range="vs-2017"
`LinesOfCode`在新的命令列程式碼度量工具中，計量更為精確且更可靠。 它與任何 codegen 差異無關，而且當工具組或執行時間變更時，並不會變更。 新工具會計算程式碼的實際行數，包括空白行和批註。
::: moniker-end

其他的度量（例如和）會 `CyclomaticComplexity` `MaintainabilityIndex` 使用與舊版 *Metrics.exe* 相同的公式，但新的工具會計算 `IOperations` (邏輯來源指令的數目，) 而非中繼語言 (IL) 指令。 這些數位將與 Visual Studio IDE 和舊版 *Metrics.exe* 所產生的數位稍有不同。

## <a name="see-also"></a>另請參閱

- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)
- [程式碼度量值](../code-quality/code-metrics-values.md)