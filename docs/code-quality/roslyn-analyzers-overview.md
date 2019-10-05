---
title: 使用 Roslyn 分析器的程式碼分析
ms.date: 03/26/2018
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: af237fbc3ce7bcf098cd47065ed18d1dfd7f20a2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975002"
---
# <a name="overview-of-net-compiler-platform-code-analyzers"></a>.NET Compiler Platform 程式碼分析器概觀

.NET Compiler Platform ("Roslyn") 分析器會基於樣式、品質與可維護性、設計和其他問題來分析程式碼。 Visual Studio 包含一組內建的分析器，可分析您輸入的 C# 和 Visual Basic 程式碼。 您會在[文字編輯器的 [選項]](../ide/code-styles-and-code-cleanup.md) 頁面上或在 [.editorconfig 檔案](../ide/editorconfig-code-style-settings-reference.md) 中設定適用於這些內建分析器的喜好設定。 您可以將其他分析器安裝為 Visual Studio 擴充功能或 NuGet 封裝。

如果分析器發現規則違規，就會在程式碼編輯器視窗和 [錯誤清單] 中回報這些違規 (於違規程式碼下方顯示為「波形曲線」)。

許多分析器規則或「診斷」都有一或多個相關聯的「程式碼修正」，可套用以修正問題。 內建於 Visual Studio 的分析器診斷各有相關聯的程式碼修正。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="net-compiler-platform-based-analysis-versus-legacy-analysis"></a>以 .NET Compiler Platform 為基礎的分析與舊版分析

.NET Compiler Platform ("Roslyn") 程式碼分析最終會取代受控程式碼的[舊版分析](../code-quality/code-analysis-for-managed-code-overview.md)。 許多舊版分析規則都已重新改寫為以 .NET Compiler Platform 為基礎的程式碼分析器。

與舊版分析規則違規相似，以 .NET Compiler Platform 為基礎的程式碼分析違規會出現在 Visual Studio [錯誤清單] 視窗中。 此外，以 .NET Compiler Platform 為基礎的程式碼分析違規也會在違規程式碼底下以「彎曲箭號」方式出現在程式碼編輯器中。 波形曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)。 下列螢幕擷取畫面顯示三個違規&mdash;一個紅色、一個綠色、一個灰色：

![程式碼編輯器中的波形曲線](media/diagnostics-severity-colors.png)

以 .NET Compiler Platform 為基礎的程式碼分析器會在建置期間分析程式碼，就跟您啟用舊版分析時一樣，但同時也會在您鍵入時進行即時分析。 若您啟用[完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#toggle-full-solution-analysis)，程式碼分析器也會在設計階段提供並未在編輯器中開啟的程式碼檔案分析。

> [!TIP]
> 只有在將分析器作為 NuGet 套件安裝時，才會顯示程式碼分析器的建置期間錯誤和警告。

以 .NET Compiler Platform 為基礎的程式碼分析器不僅會回報舊版分析所回報相同問題類型，還可以讓您輕鬆地修正檔案或專案中出現的單一或所有違規。 這些動作稱為「程式碼修正」。 程式碼修正為 IDE 特定；在 Visual Studio 中，會實作為[快速動作](../ide/quick-actions.md)。 並非所有分析器診斷都有相關聯的程式碼修正。

> [!NOTE]
> 下列 UI 選項僅適用於舊版分析：
>
> - [分析] > [執行程式碼分析] 功能表選項。
> - 專案屬性頁之 [程式**代碼分析**] 索引標籤上的 [**在組建上執行**] 和 [**隱藏產生的結果**] 核取方塊。

若要在 [錯誤清單] 視窗中區分程式碼分析器和舊版分析的違規，請查看 [工具] 欄。 若 [工具] 值與 [方案總管] 中其中一個分析器組件 (例如 **Microsoft.CodeQuality.Analyzers**) 相符，則此違規即來自程式碼分析器。 否則，違規即來自於舊版分析。

![[錯誤清單] 中的 [工具] 欄](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> 專案檔案中的 **RunCodeAnalysis** msbuild 屬性僅適用於舊版分析。 若您安裝了分析器，請在您的專案檔中將 **RunCodeAnalysis** 設為 [false]，來防止在建置後執行舊版分析。
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 套件與 VSIX 延伸模組

.NET Compiler Platform 分析器可根據每個專案透過 NuGet 套件安裝，或在 Visual Studio 中安裝為 Visual Studio 延伸模組。 這兩種[安裝分析器](../code-quality/install-roslyn-analyzers.md)的方法之間有一些重要的行為差異。

### <a name="scope"></a>`Scope`

如果您將分析器安裝為 Visual Studio 延伸模組，則會在解決方案層級套用至 Visual Studio 的所有執行個體。 如果您將分析器安裝為 NuGet 套件 (這是慣用方法)，則只會套用至安裝 NuGet 套件的專案。 在小組環境中，安裝為 NuGet 套件的分析器會將範圍限制在處理該專案的「所有開發人員」。

### <a name="build-errors"></a>建置錯誤

若要在建置期間施行規則 (包括透過命令列或作為持續整合 (CI) 組建的一部分)，請將分析器安裝為 NuGet 套件。 如果您將分析器安裝為延伸模組，則分析器警告和錯誤不會顯示在組建報告中。

下列螢幕擷取畫面顯示命令列建置輸出，其中所建置的專案包含了分析器違規：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您無法從安裝為 Visual Studio 延伸模組的分析器設定規則嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，請將分析器安裝為 NuGet 套件。

## <a name="categories"></a>Categories

以下是不同類型的分析器，可協助分析您的程式碼：

- Microsoft 推薦的分析器：[FxCop 分析器](../code-quality/fxcop-analyzers.yml)
- Visual Studio IDE 分析器：[EditorConfig](../ide/code-styles-and-code-cleanup.md)
- 第三方分析器：[StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、[Roslynator](https://www.nuget.org/packages/Roslynator/)、[XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)、[聲納分析器](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝程式碼分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.md)
- [撰寫您自己的程式碼分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
