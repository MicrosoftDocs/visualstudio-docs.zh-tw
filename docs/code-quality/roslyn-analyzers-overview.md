---
title: 在 Visual Studio 中的 Roslyn 分析器
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511418"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET Compiler Platform 分析器的概觀

Visual Studio 2017 包含一組內建分析 C# 或 Visual Basic 程式碼，當您輸入的.NET Compiler Platform 分析器。 可以安裝其他的分析器為 Visual Studio 延伸模組，或根據每個專案，NuGet 套件的形式。 分析器會尋找在程式碼樣式、 程式碼品質和可維護性、 程式碼設計，以及其他問題。

如果分析器所找不到規則違規，則會回報兩者都在做為程式碼編輯器*曲線*下方違規的程式碼，然後在**錯誤清單**。

許多的分析器規則，或*診斷*，有一或多個相關聯*程式碼修正*，您可以套用修正問題。 內建於 Visual Studio analyzer 診斷有相關聯的程式碼修正。 會顯示燈泡圖示的功能表，以及其他類型的程式碼修正*快速動作*。 這些程式碼修正的相關資訊，請參閱[一般快速動作](../ide/common-quick-actions.md)。

![分析器的違規情況並快速動作的程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>與靜態程式碼分析的 Roslyn 分析器

最終會取代.NET 編譯器平台 ("Roslyn") 的分析器[靜態程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)managed 程式碼。 已將許多的靜態程式碼分析規則改寫為 Roslyn 分析器診斷中。

Roslyn 分析器違規出現在靜態程式碼分析規則的違規，像是**錯誤清單**。 此外，Roslyn 分析器違規也會出現在程式碼編輯器中，依*曲線*違規的程式碼底下。 曲線的色彩取決於[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)的規則。 下列螢幕擷取畫面顯示三個違規&mdash;一個紅色、 一個綠色和一個灰色：

![程式碼編輯器中的曲線](media/diagnostics-severity-colors.png)

Roslyn 分析器會在建置階段，例如靜態程式碼分析，如果它已啟用，但也您鍵入即時進行分析的程式碼 ！ Roslyn 分析器也可以提供的程式碼檔案不是在編輯器中開啟，如果您啟用的設計階段 analysis[完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)。

> [!NOTE]
> 建置時間錯誤和警告的 Roslyn 分析器會顯示只有是否分析器會安裝為 NuGet 套件。

不只執行 Roslyn 分析器會報告相同類型的問題，靜態程式碼分析會執行，但可輕鬆為您修正下列一個或所有檔案或專案中的違規情況的發生次數。 這些動作稱為*程式碼修正*。 程式碼修正是 IDE 專屬;在 Visual Studio 中，它們會實作為[快速動作](../ide/quick-actions.md)。 並非所有的分析器診斷有相關聯的程式碼修正。

> [!NOTE]
> 功能表選項**分析** > **執行程式碼分析**適用於僅為靜態程式碼分析。 此外，在專案的**程式碼分析**屬性頁上，**建置時啟用程式碼分析**並**隱藏所產生的程式碼的結果**核取方塊只適用於靜態程式碼分析。 它們不影響 Roslyn 分析器。

區分從 Roslyn 分析器的違規和靜態程式碼分析**錯誤清單**，看看**工具**資料行。 如果工具 的值符合中的分析器組件的其中一個**方案總管 中**，例如**Microsoft.CodeQuality.Analyzers**，違規來自 Roslyn 分析器。 否則，違規來自靜態程式碼分析。

![工具錯誤清單中的資料行](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>VSIX 擴充功能與 NuGet 套件

.NET compiler Platform 分析器可以是會安裝每個專案透過 NuGet 套件或 Visual Studio 全為 Visual Studio 擴充功能。 有這兩種方法的某些索引鍵的行為差異[安裝分析器](../code-quality/install-roslyn-analyzers.md)。

### <a name="scope"></a>範圍

如果您安裝分析器做為 Visual Studio 擴充功能時，它們適用於在解決方案層級的 Visual Studio 的所有執行個體。 如果您將分析器安裝為 NuGet 套件，這是慣用的方法，它們只適用於已安裝 NuGet 套件的專案。 範圍中，在小組環境中，會安裝為 NuGet 套件的分析器*所有開發人員*，作用於該專案。

### <a name="build-errors"></a>建置錯誤

若要能夠在建置階段，包括透過命令列，或做為一部分的連續整合 (CI) 組建，強制執行規則安裝 NuGet 套件形式的分析器。 分析器警告和錯誤不會顯示在建置報告，如果您安裝延伸模組的分析器。

下列螢幕擷取畫面顯示建置專案，其中包含分析器規則的違規情況的命令列組建輸出：

![MSBuild 輸出與規則違規](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則嚴重性

您無法從已安裝為 Visual Studio 延伸模組的分析器設定規則的嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，安裝為 NuGet 套件的分析器。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [在 Visual Studio 中安裝 Roslyn 分析器](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的快速動作](../ide/quick-actions.md)
- [撰寫您自己的 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET 編譯器平台 SDK](/dotnet/csharp/roslyn-sdk/)