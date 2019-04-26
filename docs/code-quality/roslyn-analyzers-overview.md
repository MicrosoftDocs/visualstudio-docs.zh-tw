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
ms.openlocfilehash: ba1529840a38a23929b9926cc4bed5cc22a058cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825457"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET Compiler Platform 分析器概觀

.NET Compiler Platform ("Roslyn") 分析器會基於樣式、品質與可維護性、設計和其他問題來分析程式碼。 Visual Studio 包含一組內建的分析器，可分析您輸入的 C# 和 Visual Basic 程式碼。 您會在[文字編輯器的 [選項]](../ide/code-styles-and-quick-actions.md) 頁面上或在 [.editorconfig 檔案](../ide/editorconfig-code-style-settings-reference.md) 中設定適用於這些內建分析器的喜好設定。 您可以將其他分析器安裝為 Visual Studio 擴充功能或 NuGet 封裝。

如果分析器發現規則違規，就會在程式碼編輯器 (將違規的程式碼加上「曲線」) 和 [錯誤清單] 視窗中回報這些違規。

許多分析器規則或「診斷」都有一或多個相關聯的「程式碼修正」，可套用以修正問題。 內建於 Visual Studio 的分析器診斷各有相關聯的程式碼修正。 程式碼修正會顯示在燈泡圖示功能表中，並顯示其他類型的[快速動作](../ide/quick-actions.md)。 如需這些程式碼修正的資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn 分析器與靜態程式碼分析

.NET Compiler Platform ("Roslyn") 分析器最終會取代受控程式碼的[靜態程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)。 許多靜態程式碼分析規則已重寫為 Roslyn 分析器診斷。

如同靜態程式碼分析規則違規，Roslyn 分析器違規會出現在 [錯誤清單] 中。 此外，Roslyn 分析器違規也會顯示於程式碼編輯器中，並將違反的程式碼加上「曲線」。 曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)。 下列螢幕擷取畫面顯示三個違規&mdash;一個紅色、一個綠色、一個灰色：

![程式碼編輯器中的曲線](media/diagnostics-severity-colors.png)

Roslyn 分析器會在建置期間分析程式碼，如同靜態程式碼分析 (如已啟用)，但也會在您輸入時即時分析。 如果您啟用[完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)，Roslyn 分析器也會針對編輯器中未開啟的程式碼檔案提供設計階段分析。

> [!TIP]
> 只有在 Roslyn 分析器安裝為 NuGet 套件時，才會顯示分析器的建置期間錯誤和警告。

Roslyn 分析器不只會回報靜態程式碼分析所回報的相同問題類型，還可讓您輕鬆地修正檔案或專案中違規或所有出現的違規。 這些動作稱為「程式碼修正」。 程式碼修正為 IDE 特定；在 Visual Studio 中，會實作為[快速動作](../ide/quick-actions.md)。 並非所有分析器診斷都有相關聯的程式碼修正。

> [!NOTE]
> 下列 UI 選項僅適用於靜態程式碼分析：
>
> - [分析] > [執行程式碼分析] 功能表選項。
> - 專案屬性頁的 [程式碼分析] 索引標籤上的[建置時啟用程式碼分析] 和 [隱藏所產生程式碼的結果] 核取方塊 (這些選項對 Roslyn 分析器沒有影響)。

若要區分 [錯誤清單] 中的違規是來自 Roslyn 分析器或靜態程式碼分析，請參閱 [工具] 欄。 如果 [工具] 值符合 [方案總管] 中的其中一個分析器組件 (例如 **Microsoft.CodeQuality.Analyzers**)，則違規來自 Roslyn 分析器。 否則，違規來自靜態程式碼分析。

![[錯誤清單] 中的 [工具] 欄](media/code-analysis-tool-in-error-list.png)

> [!TIP]
> 專案檔中的 **RunCodeAnalysis** msbuild 屬性僅套用於靜態程式碼分析。 如果安裝了分析器，請在專案檔中將 **RunCodeAnalysis** 設定為 **false**，以防止靜態程式碼分析在建置之後執行。
>
> ```xml
> <RunCodeAnalysis>false</RunCodeAnalysis>
> ```

## <a name="nuget-package-versus-vsix-extension"></a>NuGet 套件與 VSIX 延伸模組

.NET Compiler Platform 分析器可根據每個專案透過 NuGet 套件安裝，或在 Visual Studio 中安裝為 Visual Studio 延伸模組。 這兩種[安裝分析器](../code-quality/install-roslyn-analyzers.md)的方法之間有一些重要的行為差異。

### <a name="scope"></a>範圍

如果您將分析器安裝為 Visual Studio 延伸模組，則會在解決方案層級套用至 Visual Studio 的所有執行個體。 如果您將分析器安裝為 NuGet 套件 (這是慣用方法)，則只會套用至安裝 NuGet 套件的專案。 在小組環境中，安裝為 NuGet 套件的分析器會將範圍限制在處理該專案的「所有開發人員」。

### <a name="build-errors"></a>建置錯誤

若要在建置期間施行規則 (包括透過命令列或作為持續整合 (CI) 組建的一部分)，請將分析器安裝為 NuGet 套件。 如果您將分析器安裝為延伸模組，則分析器警告和錯誤不會顯示在組建報告中。

下列螢幕擷取畫面顯示命令列建置輸出，其中所建置的專案包含了分析器違規：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您無法從安裝為 Visual Studio 延伸模組的分析器設定規則嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，請將分析器安裝為 NuGet 套件。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝 Roslyn 分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.md)
- [撰寫您自己的 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)