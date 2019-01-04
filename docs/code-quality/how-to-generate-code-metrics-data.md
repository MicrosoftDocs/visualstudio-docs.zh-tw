---
title: 從 IDE 或命令列產生程式碼度量
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96b74421d638a99823399a0049b712bc6c54c8a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849054"
---
# <a name="how-to-generate-code-metrics-data"></a>HOW TO：產生程式碼度量資料

您可以產生一或多個專案或整個解決方案的程式碼度量資訊結果。 程式碼度量可供 Visual Studio 互動式開發環境 (IDE) 內，以及針對C#和 Visual Basic 專案，在命令列。

此外，您可以安裝[NuGet 套件](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01)包含四個程式碼度量[分析器](roslyn-analyzers-overview.md)規則：CA1501、 CA1502、 ca1505 應及 CA1506。 根據預設，會停用這些規則，但您也可以將它們從啟用**方案總管**或是在[規則集](using-rule-sets-to-group-code-analysis-rules.md)檔案。

## <a name="visual-studio-ide-code-metrics"></a>Visual Studio IDE 的程式碼度量

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>產生整個方案的程式碼度量結果

您可以使用下列任一方式來產生整個方案的程式碼度量結果：

- 從功能表列中，選擇**分析** > **計算程式碼度量** > **方案**。

- 在 **方案總管**，以滑鼠右鍵按一下方案，然後選擇**計算程式碼度量**。

- 在 **程式碼度量結果** 視窗中，選擇**計算方案的程式碼度量** 按鈕。

就會產生結果和**程式碼度量結果** 視窗隨即顯示。 若要檢視結果的詳細資訊，請展開 樹狀目錄中的**階層**資料行。

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>產生一個或多個專案的程式碼度量結果

1. 在 [**方案總管] 中**，選取一或多個專案。

1. 從功能表列中，選擇**分析** > **計算程式碼度量** > **針對選取的專案**。

就會產生結果和**程式碼度量結果** 視窗隨即顯示。 若要檢視結果的詳細資訊，請展開 樹狀目錄中的**階層**。

## <a name="command-line-code-metrics"></a>命令列程式碼度量

您可以從命令列來產生程式碼計量資料C#和.NET Framework、.NET Core 和.NET Standard 的應用程式的 Visual Basic 專案。 命令列程式碼度量工具稱為*Metrics.exe*。

若要取得*Metrics.exe*可執行檔，必須[自行產生](#generate-the-executable)。 在不久的將來，[已發佈的版本*Metrics.exe*可](https://github.com/dotnet/roslyn-analyzers/issues/1756)讓您不必自行建置。

### <a name="generate-the-executable"></a>產生可執行檔

若要產生可執行檔*Metrics.exe*，請遵循下列步驟：

1. 複製品[dotnet/roslyn 分析器](https://github.com/dotnet/roslyn-analyzers)存放庫。
2. 系統管理員身分開啟 Visual studio 的開發人員命令提示字元。
3. 從根目錄**roslyn 分析器**存放庫中，執行下列命令： `Restore.cmd`
4. 將目錄變更為*src\Tools*。
5. 執行下列命令來建置**Metrics.csproj**專案：

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   為可執行檔*Metrics.exe*就會發出*artifacts\bin*存放庫根目錄下的目錄。

   > [!TIP]
   > 若要建置*Metrics.exe*中[舊版模式](#legacy-mode)，執行下列命令：
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>使用量

若要執行*Metrics.exe*、 提供專案或方案，輸出 XML 檔案做為引數。 例如: 

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>輸出

產生的 XML 輸出的格式如下：

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>工具的差異

舊版的 Visual Studio 中，包括 Visual Studio 2015 中，包含名為的命令列程式碼度量工具*Metrics.exe*。 這個舊版本的工具沒有二進位檔的分析，也就是組件為基礎的分析。 新的工具會改為分析原始程式碼。 因為新*Metrics.exe*是原始碼程式碼為基礎，結果就不同舊版所產生的內容*Metrics.exe*和 Visual Studio 2017 IDE 內。

新*Metrics.exe*工具可以計算即使來源的程式碼錯誤的度量，只要載入方案和專案。

#### <a name="metric-value-differences"></a>度量值的差異

`LinesOfCode`計量是更精確且可靠，在新*Metrics.exe*。 它是獨立於任何 codegen 差異並不會變更為工具組或執行階段變更時。 新*Metrics.exe*計算實際的程式碼，包括空白的行和註解的行。

其他計量，例如`CyclomaticComplexity`並`MaintainabilityIndex`使用相同的公式為舊版*Metrics.exe*，但新*Metrics.exe*計算的數目`IOperations`（邏輯來源指示） 而非中繼語言 (IL) 指令。 數字將會從舊版的稍有不同*Metrics.exe*以及從 Visual Studio 2017 IDE 的程式碼度量結果。

### <a name="legacy-mode"></a>傳統模式

您也可以選擇建置*Metrics.exe*中*舊版模式*。 舊版模式版本的工具會產生較接近工具產生何種舊版的度量值。 此外，在舊版模式下， *Metrics.exe*相同方法的集合類型，舊版的工具產生的程式碼度量資訊會產生程式碼度量資訊。 比方說，它不會產生程式碼度量資料欄位和屬性的初始設定式。 基於回溯相容性，或如果您有閘道簽入的程式碼程式碼度量數字，則舊版模式會很有用。 命令，以建置*Metrics.exe*處於傳統模式：

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

如需詳細資訊，請參閱 <<c0> [ 啟用傳統模式產生程式碼度量](https://github.com/dotnet/roslyn-analyzers/pull/1841)。

## <a name="see-also"></a>另請參閱

- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)
- [程式碼度量值](../code-quality/code-metrics-values.md)
