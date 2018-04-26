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
ms.openlocfilehash: aaa989347744e015b90cca186c6aa9756dfe90fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET 編譯器平台分析器的概觀

Visual Studio 2017 包含一組內建分析 C# 或 Visual Basic 程式碼，當您輸入的.NET 編譯器平台分析器。 可以安裝其他的分析器做為 Visual Studio 擴充功能，或根據每個專案，以 NuGet 套件。 分析器查看程式碼樣式、 程式碼品質和可維護性、 程式碼設計，以及其他問題。

如果分析器發現規則違規，則會報告在程式碼編輯器中做為*曲線*在違規程式碼，然後在**錯誤清單**。

許多分析器規則，或*診斷*，有一個或多個相關聯*程式碼修正*您可以套用到更正問題。 Visual Studio 內建的分析器診斷有相關聯的程式碼修正。 顯示燈泡圖示功能表上，以及其他類型的程式碼修正*快速控制項目*。 這些程式碼修正的相關資訊，請參閱[一般的快速動作](../ide/common-quick-actions.md)。

![分析器違規和快速動作程式碼修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn 分析器與靜態程式碼分析

.NET 編譯器平台 ("Roslyn") 分析器最終會取代[靜態程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)managed 程式碼。 已將靜態程式碼分析規則的許多改寫為 Roslyn 分析器診斷中。

靜態程式碼分析規則的違規，像是 Roslyn 分析器違規會出現在**錯誤清單**。 此外，Roslyn 分析器違規也會顯示在程式碼編輯器中，依*曲線*違規的程式碼下。 曲線的色彩取決於[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)的規則。 下列螢幕擷取畫面會顯示三個違規&mdash;一個紅色、 一個綠色和一個灰色：

![程式碼編輯器中的曲線](media/diagnostics-severity-colors.png)

Roslyn 分析器在建置時，例如如果它已啟用，但也即時當您輸入的靜態程式碼分析，分析程式碼 ！ Roslyn 分析器也可以提供設計階段分析的程式碼檔案不是在編輯器中開啟，如果您啟用[完整解決方案分析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)。

> [!NOTE]
> 建置時間錯誤和警告 Roslyn 分析器從時才會顯示是否分析器會安裝為 NuGet 封裝。

Roslyn 分析器並報告相同類型的問題會執行靜態程式碼分析，不僅能讓您輕鬆地修正下列一個或所有違規，您的檔案或專案中的項目。 這些動作稱為*程式碼修正*。 程式碼修正為 IDE 專用;在 Visual Studio 中，它們會實作為[快速控制項目](../ide/quick-actions.md)。 並非所有的分析器診斷有相關聯的程式碼修正。

> [!NOTE]
> 功能表選項**分析** > **執行程式碼分析**適用於僅為靜態程式碼分析。 此外，在專案的**程式碼分析**屬性頁**建置時啟用程式碼分析**和**隱藏來自產生的程式碼的結果**核取方塊只適用於靜態程式碼分析。 它們有 Roslyn 分析器不會影響。

區分從 Roslyn 分析器違規和靜態程式碼分析中的**錯誤清單**，看看**工具**資料行。 如果工具值符合分析器組件中的其中一個**方案總管 中**，例如**Microsoft.CodeQuality.Analyzers**，違規來自 Roslyn 分析器。 否則，違規源自靜態程式碼分析。

![工具錯誤清單中的資料行](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>相對於擴充功能的 NuGet 封裝

分析器可以是.NET 編譯器平台會安裝每個專案透過 NuGet 封裝或 Visual Studio 全為 Visual Studio 擴充功能。 有一些行為差異，這兩種方法之間[安裝分析器](../code-quality/install-roslyn-analyzers.md)。

### <a name="scope"></a>範圍

如果您安裝 Visual Studio 擴充功能分析器，它們適用於在解決方案層級的 Visual Studio 的所有執行個體。 如果您安裝分析器以 NuGet 套件，這是慣用的方法，僅會套用至安裝 NuGet 封裝的專案。 在小組環境中，安裝 NuGet 封裝為分析器會在的範圍*所有開發人員*該專案上執行的工作。

### <a name="build-errors"></a>建置錯誤

若要在建置階段，包括透過命令列或一部分持續整合 (CI) 組建，強制執行規則安裝分析器以 NuGet 套件。 分析器警告和錯誤不會顯示在組建報告如果您安裝擴充功能分析器。

下列螢幕擷取畫面顯示建置專案，其中包含的分析器規則違規的命令列組建輸出：

![MSBuild 輸出規則違規](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>規則的嚴重性

您無法從安裝為 Visual Studio 擴充功能分析器設定規則的嚴重性。 若要設定[規則嚴重性](../code-quality/use-roslyn-analyzers.md#rule-severity)，以 NuGet 套件安裝分析器。

## <a name="next-steps"></a>後續步驟

- [安裝 Visual Studio 中的 Roslyn 分析器](../code-quality/install-roslyn-analyzers.md)
- [在 Visual Studio 中使用 Roslyn 分析器](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的快速動作](../ide/quick-actions.md)
- [撰寫您自己 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET 編譯器平台 SDK](/dotnet/csharp/roslyn-sdk/)