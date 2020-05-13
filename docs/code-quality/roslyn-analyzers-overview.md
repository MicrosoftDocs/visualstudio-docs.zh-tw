---
title: 使用 Roslyn 分析器的程式碼分析
ms.date: 10/03/2019
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78a47cb2a5aefd7d20e0b8087f5f3ad735716175
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "79431276"
---
# <a name="overview-of-source-code-analyzers"></a>原始程式碼分析器概述

.NET 編譯器平臺 （"Roslyn"） 代碼分析器檢查您的 C# 或 Visual Basic 代碼，瞭解樣式、品質和可維護性、設計和其他問題。

- 某些分析器內置於視覺化工作室中。 這些分析器的診斷 ID 或代碼是 IDExxxx 格式，例如 IDE0067。 大多數這些內置分析器檢查[代碼樣式](../ide/code-styles-and-code-cleanup.md)，您可以在[文字編輯器選項頁](../ide/code-styles-and-code-cleanup.md)或[編輯器設定檔中](../ide/editorconfig-code-style-settings-reference.md)配置首選項。 少數內置分析器查看代碼品質。

- 您可以將其他分析器安裝為 NuGet 包或 Visual Studio 擴展。 例如：

  - [FxCop 分析儀](../code-quality/install-fxcop-analyzers.md)，微軟推薦的代碼品質分析儀
  - 協力廠商分析儀，如[StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)StyleCop、Roslynator、XUnit[分析儀](https://www.nuget.org/packages/xunit.analyzers/)和[聲納分析儀](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)[ ](https://www.nuget.org/packages/Roslynator.Analyzers/)

如果分析器發現規則衝突，則在代碼編輯器（作為違規代碼下的*波浪*）和"錯誤清單"視窗中報告它們。

許多分析器規則或「診斷」** 都有一或多個相關聯的「程式碼修正」**，可套用以修正問題。 內建於 Visual Studio 的分析器診斷各有相關聯的程式碼修正。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="source-code-analysis-versus-legacy-analysis"></a>原始程式碼分析與舊版分析

Roslyn 分析器的源分析取代了託管代碼[的舊分析](../code-quality/code-analysis-for-managed-code-overview.md)。 許多舊分析規則已被重寫為 Roslyn 代碼分析器。 對於較新的專案範本（如 .NET Core 和 .NET 標準專案），即使舊版分析也不可用。

與舊版分析規則衝突一樣，原始程式碼分析衝突也顯示在 Visual Studio 中的"錯誤清單"視窗中。 此外，原始程式碼分析衝突也會在代碼編輯器中顯示為違規代碼下的*波浪。* 波形曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)。 下圖顯示了三個衝突&mdash;，一個是紅色、一個綠色和一個灰色：

![視覺工作室中的代碼編輯器中的晃動](media/diagnostics-severity-colors.png)

代碼分析器在生成時檢查代碼，如舊版分析（如果啟用了代碼），但在鍵入時也即時進行。 您可以將即時代碼分析的範圍配置為僅針對當前文檔、所有打開的文檔或整個解決方案執行。 請參閱[如何：配置即時代碼分析的範圍](./configure-live-code-analysis-scope-managed-code.md)。

> [!TIP]
> 只有在將分析器作為 NuGet 套件安裝時，才會顯示程式碼分析器的建置期間錯誤和警告。 內置分析器（例如 IDE0067 和 IDE0068）在生成期間從不運行。

Roslyn 代碼分析器不僅報告與舊版分析相同的問題類型，而且使您能夠輕鬆修復檔或專案中的一個或所有衝突發生。 這些動作稱為「程式碼修正」**。 代碼修復特定于 IDE;在視覺工作室中，它們被實現為["快速操作](../ide/quick-actions.md)"。 並非所有分析器診斷都有相關聯的程式碼修正。

> [!NOTE]
> 在 Visual Studio 2019 16.5 版本之前，**分析** > **運行代碼分析**功能表選項執行舊版分析。 從 Visual Studio 2019 16.5 開始，**運行代碼分析**功能表選項將執行基於 Roslyn 的基於 Roslyn 的分析器，用於所選項目或解決方案。

要區分錯誤清單中的代碼分析器和遺留分析的違規情況，請查看 **"工具"** 列。 若 [工具] 值與 [方案總管]**** 中其中一個分析器組件 (例如 **Microsoft.CodeQuality.Analyzers**) 相符，則此違規即來自程式碼分析器。 否則，違規即來自於舊版分析。

![[錯誤清單] 中的 [工具] 欄](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> 專案檔案中的**RunCodeAnalysis** MSBuild 屬性僅適用于舊版分析。 如果安裝分析器，請將**RunCodeAnalysis**設置為專案檔案中**的 false，** 以防止生成後運行舊分析。
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 套件與 VSIX 延伸模組

Roslyn 代碼分析儀可通過 NuGet 包按專案安裝。 有些還可以作為 Visual Studio 擴展，在這種情況下，它們適用于您在 Visual Studio 中打開的任何解決方案。 這兩種[安裝分析器](../code-quality/install-roslyn-analyzers.md)的方法之間有一些重要的行為差異。

### <a name="scope"></a>影響範圍

如果將分析器安裝為 Visual Studio 擴展，則它們將應用於解決方案級別和 Visual Studio 的所有實例。 如果您將分析器安裝為 NuGet 套件 (這是慣用方法)，則只會套用至安裝 NuGet 套件的專案。 在小組環境中，安裝為 NuGet 套件的分析器會將範圍限制在處理該專案的「所有開發人員」**。

### <a name="build-errors"></a>建置錯誤

若要在建置期間施行規則 (包括透過命令列或作為持續整合 (CI) 組建的一部分)，請將分析器安裝為 NuGet 套件。 如果您將分析器安裝為延伸模組，則分析器警告和錯誤不會顯示在組建報告中。

下圖顯示了生成包含分析器規則衝突的專案的命令列生成輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您不能從作為 Visual Studio 擴展安裝的分析器中配置規則的嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，請將分析器安裝為 NuGet 套件。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝程式碼分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.md)
- [撰寫您自己的程式碼分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)
