---
title: FxCop 程式碼分析和 FxCop 分析器
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: dffc3773714336162b3b863fa03a6964b68a3673
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649589"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop 和 FxCop 分析器的相關常見問題

舊版 FxCop 與 FxCop 分析器之間的差異可能有點令人難以了解。 本文旨在解決您可能會遇到的一些問題。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>舊版 FxCop 與 FxCop 分析器之間有何差異？

舊版 FxCop 會對已編譯的組件執行建置後分析。 它會作為獨立可執行檔 **FxCopCmd.exe** 來執行。 FxCopCmd.exe 會載入已編譯的組件、執行程式碼分析，然後回報結果 (或「診斷」)。

FxCop 分析器是以 .NET Compiler Platform ("Roslyn") 為基礎。 您可以[將分析器安裝為 NuGet 套件](install-fxcop-analyzers.md#nuget-package)，以供專案或方案參考。 FxCop 分析器會在編譯器執行期間執行以原始程式碼為基礎的分析。 FxCop 分析器是裝載於編譯器處理序 **csc.exe** 或 **vbc.exe** 內，並在建置專案時執行分析。 分析器結果會與編譯器結果一併回報。

> [!NOTE]
> 您也可以[將 FxCop 分析器安裝為 Visual Studio 延伸模組](install-fxcop-analyzers.md#vsix)。 在此情況下，分析器會在您於程式碼編輯器中鍵入時執行，但不會在建置期間執行。 若要將 FxCop 分析器當作持續整合 (CI) 的一部分來執行，請將其改安裝為 NuGet 套件。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>[執行程式碼分析] 命令是否會執行 FxCop 分析器？

否。 當您選取 **分析** > **執行程式碼分析**時，它會執行舊版分析。 [執行程式碼分析] 不會影響 Roslyn 型分析器，包括 Roslyn 型 FxCop 分析器。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 專案屬性是否會執行分析器？

否。 專案檔中的 **RunCodeAnalysis** 屬性 (例如 *.csproj*) 只會用來執行舊版 FxCop。 它會執行建置後 msbuild 工作，以叫用 **FxCopCmd.exe**。 這相當於在 Visual Studio 中選取 [分析] > [執行程式碼分析]。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>那麼要如何執行 FxCop 分析器？

若要執行 FxCop 分析器，請先為其[安裝 NuGet 套件](install-fxcop-analyzers.md)。 然後從 Visual Studio 或使用 msbuild 建置您的專案或方案。 FxCop 分析器產生的警告和錯誤會出現在 [錯誤清單] 或命令視窗中。

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>即使我安裝了 FxCop 分析器 NuGet 套件，我也會收到警告 CA0507

如果您已安裝 FxCop 分析器，但繼續取得警告 CA0507 「**執行程式碼分析」已被取代，而是在組建期間執行 fxcop 分析器，** 則您可能需要在專案中設定**RunCodeAnalysis** msbuild 屬性[檔案設為](../ide/solutions-and-projects-in-visual-studio.md#project-file) **false**。 否則，會在每個組建之後執行舊版分析。

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>哪些規則已移植到 FxCop 分析器？

如需哪些舊版分析規則已移植到[fxcop 分析器](install-fxcop-analyzers.md)的詳細資訊，請參閱[fxcop 規則埠狀態](fxcop-rule-port-status.md)。

## <a name="code-analysis-warnings-are-treated-as-errors"></a>程式碼分析警告會視為錯誤

如果您的專案使用 build 選項將警告視為錯誤，則 FxCop 分析器警告可能會顯示為錯誤。 若要防止程式碼分析警告被視為錯誤，請遵循程式[代碼分析常見問題](../code-quality/analyzers-faq.md#treat-warnings-as-errors)中的步驟。

## <a name="see-also"></a>請參閱

- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [開始使用分析器](fxcop-analyzers.yml)
- [安裝 FxCop 分析器](install-fxcop-analyzers.md)
