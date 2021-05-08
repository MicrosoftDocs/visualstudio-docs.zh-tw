---
title: 'FxCop 程式碼分析 (二進位分析) 和 .NET 分析器 (來源分析) '
ms.date: 09/06/2018
description: 瞭解 Visual Studio 中舊版 FxCop (二進位分析) 和 .NET 分析器 (來源分析) 之間的差異。 請參閱有關如何使用這些分析器的問題答案。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis FAQ
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 951e9b951f1d90077fe29506e9c288fb19f2d5ff
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108800473"
---
# <a name="frequently-asked-questions-about-legacy-fxcop-and-net-analyzers"></a>舊版 FxCop 和 .NET 分析器的常見問題

瞭解舊版 FxCop (二進位分析) 和 .NET 分析器 (來源分析) 之間的差異，可能會有點混淆。 本文旨在解決您可能會遇到的一些問題。

## <a name="whats-the-difference-between-legacy-fxcop-and-net-analyzers"></a>舊版 FxCop 和 .NET 分析器之間有何差異？

舊版 FxCop 會對已編譯的組件執行建置後分析。 它會作為獨立可執行檔 **FxCopCmd.exe** 來執行。 FxCopCmd.exe 會載入已編譯的組件、執行程式碼分析，然後回報結果 (或「診斷」)。

.NET 分析器是以 .NET Compiler Platform ( "Roslyn" ) 為基礎。 您可以 [從 .NET SDK 啟用它們，或將它們安裝為](install-net-analyzers.md) 專案或解決方案所參考的 NuGet 套件。 分析器會在編譯器執行期間執行以程式碼為基礎的分析。 分析器裝載于編譯器進程內（ **csc.exe** 或 **vbc.exe**），並在建立專案時執行分析。 分析器結果會與編譯器結果一併回報。

## <a name="whats-the-difference-between-fxcop-analyzers-and-net-analyzers"></a>FxCop 分析器和 .NET 分析器之間有何差異？

FxCop 分析器和 .NET 分析器都會參考 FxCop CA 規則 ) 分析器的 .NET Compiler Platform ( "Roslyn"。 在 Visual Studio 2019 16.8 和 .NET 5.0 之前，這些分析器會以 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的形式傳送。 從 Visual Studio 2019 16.8 和 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](/dotnet/fundamentals/code-analysis/overview)。 它們也可以作為 `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)。 請考慮 [從 FxCop 分析器遷移至 .net 分析器](migrate-from-fxcop-analyzers-to-net-analyzers.md)。

## <a name="does-the-run-code-analysis-command-run-net-analyzers"></a>[執行程式碼分析] 命令是否執行 .NET 分析器？

在 Visual Studio 2019 16.5 版之前，當您選取 [**分析**  >  **執行程式碼分析**] 時，會執行舊版分析。 從 2019 16.5 開始 Visual Studio，[ **執行程式碼分析** ] 功能表選項會針對選取的專案或方案執行以 Roslyn 為基礎的分析器。 如果您已安裝 .NET 分析器，也會執行它們。 如需詳細資訊，請參閱 [如何：針對 Managed 程式碼手動執行程式碼分析](how-to-run-code-analysis-manually-for-managed-code.md)。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 專案屬性是否會執行分析器？

不會。 專案檔中的 **RunCodeAnalysis** 屬性 (例如 *.csproj*) 只會用來執行舊版 FxCop。 它會執行建置後 msbuild 工作，以叫用 **FxCopCmd.exe**。

## <a name="so-how-do-i-run-net-analyzers-then"></a>那麼，我該如何執行 .NET 分析器呢？

若要執行 .NET 分析器，請先 [從 .NET SDK 啟用它們，或將它們安裝為 NuGet 套件](install-net-analyzers.md)。 然後從 Visual Studio 或使用 msbuild 建置您的專案或方案。 Roslyn 分析器產生的警告和錯誤會出現在 [ **錯誤清單** ] 或 [命令] 視窗中。

## <a name="i-get-warning-ca0507-even-after-ive-installed-the-net-analyzers-nuget-package"></a>即使我已安裝 .NET 分析器 NuGet 套件，也會收到警告 CA0507

如果您已安裝 .NET 分析器，但仍繼續取得警告 CA0507 「**執行程式碼分析」已被取代為使用在組建期間執行的 FxCop 分析器**」，則您可能需要將 [專案](../ide/solutions-and-projects-in-visual-studio.md#project-file)檔中的 [ **>runcodeanalysis** msbuild] 屬性設定為 [ **false**]。 否則，會在每個組建之後執行舊版分析。

```xml
<RunCodeAnalysis>false</RunCodeAnalysis>
```

## <a name="which-rules-have-been-ported-to-net-analyzers"></a>哪些規則已移植到 .NET 分析器？

如需哪些舊版分析規則已移植到 .NET 分析器的詳細資訊，請參閱 [Fxcop 規則埠狀態](fxcop-rule-port-status.md)。

## <a name="code-analysis-warnings-are-treated-as-errors"></a>程式碼分析警告視為錯誤

如果您的專案使用 build 選項將警告視為錯誤，分析器警告可能會顯示為錯誤。 若要避免將程式碼分析警告視為錯誤，請依照程式 [代碼分析常見問題](../code-quality/analyzers-faq.md#treat-warnings-as-errors)中的步驟執行。

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [移轉至 .NET 分析器](migrate-from-legacy-analysis-to-net-analyzers.md)
- [安裝 .NET 分析器](install-net-analyzers.md)
