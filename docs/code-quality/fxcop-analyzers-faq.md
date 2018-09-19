---
title: FxCop 程式碼分析和 FxCop 分析器
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136364"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>常見問題集 FxCop 和 FxCop 分析器

它可以是有點令人困惑，以了解差異舊版 FxCop 和 FxCop 分析器。 本文旨在解決您可能會有的問題的部分。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>舊版 FxCop 和 FxCop 之間的差異為何分析器？

舊版 FxCop 執行建置後的分析已編譯的組件。 執行個別的可執行檔名**FxCopCmd.exe**。 FxCopCmd.exe 載入已編譯的組件、 執行程式碼分析，並報告結果，然後 (或*診斷*)。

FxCop 分析器根據.NET 編譯器平台 ("Roslyn")。 您[將它們安裝為 NuGet 套件](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)所參考的專案或方案。 FxCop 分析器執行原始程式碼編譯器執行期間型分析。 FxCop 分析器會是裝載於編譯器處理序**csc.exe**或是**vbc.exe**，並建置專案時，執行分析。 編譯器結果以及報告分析程式結果。

> [!NOTE]
> 您也可以[做為 Visual Studio 擴充功能安裝 FxCop 分析器](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)。 在此情況下，分析器會執行您在程式碼編輯器中，輸入，但它們不在建置階段中執行。 如果您想要執行的持續整合 (CI) 一部分的 FxCop 分析器，安裝它們以 NuGet 套件。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>執行程式碼分析命令執行 FxCop 分析器為何？

否。 當您選取**分析** > **執行程式碼分析**在 Visual Studio 2017 中，它會執行靜態程式碼分析或舊版 FxCop。 **執行程式碼分析**roslyn 分析器，包括以 Roslyn 為基礎的 FxCop 分析器對沒有任何作用。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild 專案屬性執行分析器為何？

否。 **RunCodeAnalysis**專案檔中的屬性 (例如 *.csproj*) 只會用來執行舊版 FxCop。 它會執行建置後 msbuild 工作，以叫用**FxCopCmd.exe**。 這相當於選取**分析** > **執行程式碼分析**Visual Studio 中。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>那麼要如何再執行 FxCop 分析器？

第一次執行 FxCop 分析器[安裝 NuGet 套件](install-fxcop-analyzers.md)它們。 然後從 Visual Studio 或使用 msbuild 建置專案或解決方案。 這些警告和 FxCop 分析器所產生的錯誤會出現在**錯誤清單** 或命令視窗。

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform 分析器的概觀](roslyn-analyzers-overview.md)
- [開始使用分析器](fxcop-analyzers.yml)
- [安裝 FxCop 分析器](install-fxcop-analyzers.md)
