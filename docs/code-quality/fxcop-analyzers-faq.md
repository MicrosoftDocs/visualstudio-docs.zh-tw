---
title: FxCop 程式碼分析和 FxCop 分析器
ms.date: 09/06/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc04cbc6d46d8dc47a08d06c8c5949bb5d9107f3
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431361"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop 和 FxCop 分析器的相關常見問題

舊版 FxCop 與 FxCop 分析器之間的差異可能有點令人難以了解。 本文旨在解決您可能會遇到的一些問題。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>舊版 FxCop 與 FxCop 分析器之間有何差異？

舊版 FxCop 會對已編譯的組件執行建置後分析。 它會作為獨立可執行檔 **FxCopCmd.exe** 來執行。 FxCopCmd.exe 會載入已編譯的組件、執行程式碼分析，然後回報結果 (或「診斷」**)。

FxCop 分析器是以 .NET Compiler Platform ("Roslyn") 為基礎。 您可以[將分析器安裝為 NuGet 套件](install-fxcop-analyzers.md#nuget-package)，以供專案或方案參考。 FxCop 分析器會在編譯器執行期間執行以原始程式碼為基礎的分析。 FxCop 分析器是裝載於編譯器處理序 **csc.exe** 或 **vbc.exe** 內，並在建置專案時執行分析。 分析器結果會與編譯器結果一併回報。

> [!NOTE]
> 您也可以[將 FxCop 分析器安裝為 Visual Studio 延伸模組](install-fxcop-analyzers.md#vsix)。 在此情況下，分析器會在您於程式碼編輯器中鍵入時執行，但不會在建置期間執行。 若要將 FxCop 分析器當作持續整合 (CI) 的一部分來執行，請將其改安裝為 NuGet 套件。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>[執行程式碼分析] 命令是否會執行 FxCop 分析器？

在 Visual Studio 2019 16.5 版本之前，當您選擇 **"分析** > **運行代碼分析**"時，它將執行舊版分析。 從 Visual Studio 2019 16.5 開始，**運行代碼分析**功能表選項將執行基於 Roslyn 的基於 Roslyn 的分析器，用於所選項目或解決方案。 如果您安裝了基於 Roslyn 的 FxCop 分析儀，它們也將被執行。 有關詳細資訊，請參閱[如何：手動運行託管代碼的代碼分析](how-to-run-code-analysis-manually-for-managed-code.md)。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 專案屬性是否會執行分析器？

否。 專案檔中的 **RunCodeAnalysis** 屬性 (例如 *.csproj*) 只會用來執行舊版 FxCop。 它會執行建置後 msbuild 工作，以叫用 **FxCopCmd.exe**。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>那麼要如何執行 FxCop 分析器？

若要執行 FxCop 分析器，請先為其[安裝 NuGet 套件](install-fxcop-analyzers.md)。 然後從 Visual Studio 或使用 msbuild 建置您的專案或方案。 FxCop 分析器產生的警告和錯誤會出現在 [錯誤清單]**** 或命令視窗中。

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>即使我安裝了 FxCop 分析器 NuGet 套件，我也會收到警告 CA0507

如果您已安裝 FxCop 分析器，但繼續收到警告 CA0507"**運行代碼分析"已被棄用，轉而使用在生成期間運行的 FxCop 分析器"，** 則可能需要將[專案檔案中](../ide/solutions-and-projects-in-visual-studio.md#project-file)的**RunCodeAnalysis** msbuild 屬性設置為**false**。 否則，遺留分析將在每次生成後執行。

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>哪些規則已移植到 FxCop 分析儀？

有關哪些舊版分析規則已移植到[FxCop 分析器](install-fxcop-analyzers.md)的資訊，請參閱[Fxcop 規則埠狀態](fxcop-rule-port-status.md)。

## <a name="code-analysis-warnings-are-treated-as-errors"></a>代碼分析警告被視為錯誤

如果專案使用生成選項將警告視為錯誤，則 FxCop 分析器警告可能會顯示為錯誤。 為防止將代碼分析警告視為錯誤，請按照[代碼分析常見問題 解答](../code-quality/analyzers-faq.md#treat-warnings-as-errors)中的步驟操作。

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [遷移到 FxCop 分析儀](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [安裝 FxCop 分析器](install-fxcop-analyzers.md)
