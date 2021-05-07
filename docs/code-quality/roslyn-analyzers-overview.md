---
title: 使用 Roslyn 分析器的程式碼分析
ms.date: 09/01/2020
description: 熟悉 Visual Studio 中的原始程式碼分析。 瞭解程式碼修正以及不同類型的分析器和嚴重性層級。
ms.custom: SEO-VS-2020
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
- code analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c3a7192ac55dc4138746e3e1e1abe4eaa6928395
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798332"
---
# <a name="overview-of-source-code-analysis"></a>原始程式碼分析總覽

.NET Compiler Platform (Roslyn) 分析器會檢查您的 c # 或 Visual Basic 程式碼，以取得樣式、品質、可維護性、設計和其他問題。 這項檢查或分析是在設計階段于所有開啟的檔案中完成。

分析器可以分為下列群組：

- 程式[代碼樣式](/dotnet/fundamentals/code-analysis/code-style-rule-options?preserve-view=true&view=vs-2019#convention-categories)分析器內建于 Visual Studio。 這些分析器的診斷識別碼或程式碼的格式為 IDExxxx，例如 IDE0067。 您可以在 [文字編輯器](../ide/code-styles-and-code-cleanup.md) 的 [選項] 頁面或 [EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)檔中設定喜好設定。 從 .NET 5.0 開始，程式碼樣式分析器會隨附于 .NET SDK，而且可以嚴格地強制執行為組建警告或錯誤。 如需詳細資訊，請參閱[這裡](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis)。

- 程式[代碼品質](/dotnet/fundamentals/code-analysis/quality-rules/index)分析器現在隨附于 .NET 5 SDK，而且預設為啟用。 這些分析器的診斷識別碼或程式碼的格式為 CAxxxx，例如 CA1822。 如需詳細資訊，請參閱 [.net 程式碼品質分析的總覽](/dotnet/fundamentals/productivity/code-analysis#code-quality-analysis)。

- 協力廠商分析器可以安裝為 NuGet 套件或 Visual Studio 擴充功能。 協力廠商分析器，例如 [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/)、 [Roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/)、 [XUnit 分析器](https://www.nuget.org/packages/xunit.analyzers/)和 [聲納 Analyzer](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)。

## <a name="severity-levels-of-analyzers"></a>分析器的嚴重性層級

每個分析器都有下列其中一個嚴重性層級：

| 嚴重性 (方案總管)  | 嚴重性 (EditorConfig 檔)  | 組建階段行為 | 編輯器行為 |
|-|-|-|
| 錯誤 | `error` | 違規在錯誤清單和命令列組建輸出中會顯示為 *錯誤* ，導致組建失敗。| 有問題的程式碼會以紅色波浪線加上底線，並在捲軸中以小紅色方塊標記。 |
| 警告 | `warning` | 違規在錯誤清單和命令列組建輸出中會顯示為 *警告* ，但不會造成組建失敗。 | 有問題的程式碼會以綠色波浪線加上底線，並在捲軸中以小綠色方塊標記。 |
| Info | `suggestion` | 違規會以 *訊息* 形式出現在錯誤清單中，而不是在命令列組建輸出中。 | 有問題的程式碼會以灰色波浪線加上底線，並在捲軸中以小灰色方塊標記。 |
| Hidden | `silent` | 使用者看不到。 | 使用者看不到。 不過，診斷會回報給 IDE 診斷引擎。 |
| 無 | `none` | 已完全隱藏。 | 已完全隱藏。 |
| 預設 | `default` | 對應于規則的預設嚴重性。 若要判斷規則的預設值為何，請查看屬性視窗。 | 對應于規則的預設嚴重性。 |

如果分析器發現規則違規，就會在 [程式碼編輯器] 中回報它們， (在違規程序代碼) 和 [錯誤清單] 視窗中的 *波浪* 線。

![錯誤清單視窗中的分析器違規](../code-quality/media/code-analysis-error-list.png)

錯誤清單中報告的分析器違規符合規則的 [嚴重性層級設定](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) 。 分析器違規也會在程式碼編輯器中顯示為違規程序代碼底下的波浪線。 下圖顯示三個 &mdash; 錯誤 (紅色波浪線) 、一個警告 (綠色波浪線) ，以及一個建議 (三個灰色的點) ：

![Visual Studio 中的程式碼編輯器中的波浪線](media/diagnostics-severity-colors.png)

許多分析器規則或 *診斷* 都有一或多個相關聯的程式 *代碼修正* ，可套用以修正規則違規。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="configure-analyzer-severity-levels"></a>設定分析器嚴重性層級

您可以在 [EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)檔案中或從燈泡 [功能表](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)設定分析器規則或 *診斷* 的嚴重性。

分析器也可以設定為在您輸入時，于組建階段檢查程式碼。 您可以設定即時程式碼分析的範圍，以便只針對目前檔、所有開啟的檔或整個方案執行。 請參閱 [如何：設定即時程式碼分析的範圍](./configure-live-code-analysis-scope-managed-code.md)。

> [!TIP]
> 只有在將分析器作為 NuGet 套件安裝時，才會顯示程式碼分析器的建置期間錯誤和警告。 內建的分析器 (例如，IDE0067 和 IDE0068) 絕不會在組建期間執行。

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 套件與 VSIX 延伸模組

您可以透過 NuGet 套件，針對每個專案安裝協力廠商分析器。 某些也可做為 Visual Studio 延伸模組使用，在此情況下，它們會套用至您在 Visual Studio 中開啟的任何解決方案。 這兩種[安裝分析器](../code-quality/install-roslyn-analyzers.md)的方法之間有一些重要的行為差異。

### <a name="scope"></a>影響範圍

如果您將分析器安裝為 Visual Studio 延伸模組，則會套用到方案層級和所有 Visual Studio 實例。 如果您將分析器安裝為 NuGet 套件 (這是慣用方法)，則只會套用至安裝 NuGet 套件的專案。 在小組環境中，安裝為 NuGet 套件的分析器會將範圍限制在處理該專案的「所有開發人員」。

### <a name="build-errors"></a>建置錯誤

若要在組建階段強制執行規則，包括透過命令列或作為連續整合 (CI) 組建的一部分，您可以從下列其中一個選項中選擇：

- 建立 .NET 5.0 專案，在 .NET SDK 中預設包含分析器。 根據預設，以 .NET 5.0 或更新版本為目標的專案會啟用程式碼分析。 您可以藉由將 [EnableNETAnalyzers](/dotnet/core/project-sdk/msbuild-props#enablenetanalyzers) 屬性設定為 true，對以舊版 .net 版本為目標的專案啟用程式碼分析。

- 將分析器安裝為 NuGet 套件。 如果您將分析器安裝為延伸模組，則分析器警告和錯誤不會顯示在組建報告中。

下圖顯示建立包含分析器規則違規之專案的命令列組建輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您無法從安裝為 Visual Studio 延伸模組的分析器設定規則的嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)，請將分析器安裝為 NuGet 套件。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝程式碼分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用程式碼分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.yml)
- [撰寫您自己的程式碼分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)