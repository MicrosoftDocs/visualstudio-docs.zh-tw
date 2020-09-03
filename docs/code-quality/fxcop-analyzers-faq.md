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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
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

在 Visual Studio 2019 16.5 版之前，當您選取 [**分析**  >  **執行程式碼分析**] 時，會執行舊版分析。 從 2019 16.5 開始 Visual Studio，[ **執行程式碼分析** ] 功能表選項會針對選取的專案或方案執行以 Roslyn 為基礎的分析器。 如果您已安裝以 Roslyn 為基礎的 FxCop 分析器，也會執行它們。 如需詳細資訊，請參閱 [如何：針對 Managed 程式碼手動執行程式碼分析](how-to-run-code-analysis-manually-for-managed-code.md)。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 專案屬性是否會執行分析器？

否。 專案檔中的 **RunCodeAnalysis** 屬性 (例如 *.csproj*) 只會用來執行舊版 FxCop。 它會執行建置後 msbuild 工作，以叫用 **FxCopCmd.exe**。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>那麼要如何執行 FxCop 分析器？

若要執行 FxCop 分析器，請先為其[安裝 NuGet 套件](install-fxcop-analyzers.md)。 然後從 Visual Studio 或使用 msbuild 建置您的專案或方案。 FxCop 分析器產生的警告和錯誤會出現在 [錯誤清單]**** 或命令視窗中。

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-fxcop-analyzers-nuget-package"></a>即使我安裝了 FxCop 分析器 NuGet 套件，我也會收到警告 CA0507

如果您已安裝 FxCop 分析器，但仍繼續取得警告 CA0507 「**執行程式碼分析」已被取代為使用在組建期間執行的 FxCop 分析器**」，則您可能需要將[專案](../ide/solutions-and-projects-in-visual-studio.md#project-file)檔中的 **>runcodeanalysis** msbuild 屬性設為**false**。 否則，會在每個組建之後執行舊版分析。

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-fxcop-analyzers"></a>哪些規則已移植至 FxCop 分析器？

如需哪些舊版分析規則已移植至 [fxcop 分析器](install-fxcop-analyzers.md)的詳細資訊，請參閱 [FxCop 規則埠狀態](fxcop-rule-port-status.md)。

## <a name="code-analysis-warnings-are-treated-as-errors"></a>程式碼分析警告視為錯誤

如果您的專案使用 build 選項將警告視為錯誤，則 FxCop 分析器警告可能會顯示為錯誤。 若要避免將程式碼分析警告視為錯誤，請依照程式 [代碼分析常見問題](../code-quality/analyzers-faq.md#treat-warnings-as-errors)中的步驟執行。

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [移轉到 FxCop 分析器](migrate-from-legacy-analysis-to-fxcop-analyzers.md)
- [安裝 FxCop 分析器](install-fxcop-analyzers.md)
