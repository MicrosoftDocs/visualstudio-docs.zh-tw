---
title: 使用 Roslyn 分析器的程式碼分析
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 844b9475ea59ba15ac96d3cbe19523f5cba63c72
ms.sourcegitcommit: 7825d4163e52d724e59f6c0da209af5fbef673f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999990"
---
# <a name="overview-of-source-code-analyzers"></a>原始程式碼分析器的總覽

.NET Compiler Platform （"Roslyn"）程式碼分析器會C#檢查您或 Visual Basic 的程式碼，以瞭解樣式、品質和可維護性、設計和其他問題。

- 有些分析器內建 Visual Studio。 這些分析器的診斷識別碼（或程式碼）的格式為 IDExxxx，例如 IDE0067。 大部分的內建分析器都會檢查程式[代碼樣式](../ide/code-styles-and-code-cleanup.md)，而您可以在 [[文字編輯器](../ide/code-styles-and-code-cleanup.md)] [選項] 頁面或在[EditorConfig](../ide/editorconfig-code-style-settings-reference.md)檔案中設定喜好設定。 幾個內建分析器會查看程式碼品質。

- 您可以將其他分析器安裝為 NuGet 套件或 Visual Studio 延伸模組。 例如:

  - [FxCop 分析器](../code-quality/install-fxcop-analyzers.md)，Microsoft 建議的程式碼品質分析器
  - 協力廠商分析器，例如[stylecop 能夠](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和[Sonar Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

如果分析器發現違反規則，則會在程式碼編輯器中回報（做為有問題的程式碼下的*波浪*線）和 [錯誤清單] 視窗。

許多分析器規則或「診斷」都有一或多個相關聯的「程式碼修正」，可套用以修正問題。 內建於 Visual Studio 的分析器診斷各有相關聯的程式碼修正。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>原始碼分析與舊版分析

Roslyn 分析器的來源分析會取代 managed 程式碼的[舊版分析](../code-quality/code-analysis-for-managed-code-overview.md)。 許多舊版分析規則都已經改寫為 Roslyn 程式碼分析器。 對於較新的專案範本，例如 .NET Core 和 .NET Standard 專案，舊版分析甚至無法使用。

如同舊版分析規則違規，原始程式碼分析違規會出現在 Visual Studio 的 [錯誤清單] 視窗中。 此外，原始程式碼的分析違規也會在程式碼編輯器中顯示為*波浪線*在違規程序代碼之下。 波形曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)。 下圖顯示三個違規 @ no__t-0one red、一個綠色和一個灰色：

![Visual Studio 中的程式碼編輯器中的波浪線](media/diagnostics-severity-colors.png)

程式碼分析器會在組建階段檢查程式碼，例如舊版分析（如果已啟用），但也會在您輸入時即時偵測。 若您啟用[完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis)，程式碼分析器也會在設計階段提供並未在編輯器中開啟的程式碼檔案分析。

> [!TIP]
> 只有在將分析器作為 NuGet 套件安裝時，才會顯示程式碼分析器的建置期間錯誤和警告。 內建分析器（例如，IDE0067 和 IDE0068）永遠不會在組建期間執行。

Roslyn 程式碼分析器不僅會回報舊版分析所需的相同類型問題，還可讓您輕鬆地修正檔案或專案中發生的一或多個違規。 這些動作稱為「程式碼修正」。 程式碼修正是 IDE 特有的;在 Visual Studio 中，它們會實作為[快速動作](../ide/quick-actions.md)。 並非所有分析器診斷都有相關聯的程式碼修正。

> [!NOTE]
> [**分析** > **執行程式碼分析**] 功能表選項只適用于舊版分析。

若要區別來自程式碼分析器的違規和錯誤清單中的舊版分析，請查看**Tool**資料行。 若 [工具] 值與 [方案總管] 中其中一個分析器組件 (例如 **Microsoft.CodeQuality.Analyzers**) 相符，則此違規即來自程式碼分析器。 否則，違規即來自於舊版分析。

![[錯誤清單] 中的 [工具] 欄](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> 專案檔中的**RunCodeAnalysis** MSBuild 屬性僅適用于舊版分析。 如果您安裝分析器，請在專案檔中將**RunCodeAnalysis**設定為**false** ，以避免在組建之後執行舊版分析。
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 套件與 VSIX 延伸模組

您可以透過 NuGet 套件，針對每個專案安裝 Roslyn 程式碼分析器。 有些也可以做為 Visual Studio 延伸模組，在這種情況下，它們會套用至您在 Visual Studio 中開啟的任何解決方案。 這兩種[安裝分析器](../code-quality/install-roslyn-analyzers.md)的方法之間有一些重要的行為差異。

### <a name="scope"></a>`Scope`

如果您將分析器安裝為 Visual Studio 擴充功能，它們會套用至解決方案層級和所有 Visual Studio 的實例。 如果您將分析器安裝為 NuGet 套件 (這是慣用方法)，則只會套用至安裝 NuGet 套件的專案。 在小組環境中，安裝為 NuGet 套件的分析器會將範圍限制在處理該專案的「所有開發人員」。

### <a name="build-errors"></a>建置錯誤

若要在建置期間施行規則 (包括透過命令列或作為持續整合 (CI) 組建的一部分)，請將分析器安裝為 NuGet 套件。 如果您將分析器安裝為延伸模組，則分析器警告和錯誤不會顯示在組建報告中。

下圖顯示建立包含分析器規則違規之專案的命令列組建輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您無法從安裝為 Visual Studio 擴充功能的分析器設定規則的嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，請將分析器安裝為 NuGet 套件。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝程式碼分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.md)
- [撰寫您自己的程式碼分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
