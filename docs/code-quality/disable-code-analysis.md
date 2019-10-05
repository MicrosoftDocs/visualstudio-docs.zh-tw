---
title: 關閉程式碼分析
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 77c189e4a15f2ae4049c45d2c8463079895f5be2
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975152"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>如何停用 managed 程式碼的原始程式碼分析

::: moniker range=">=vs-2019"

此頁面可協助您停用 Visual Studio 中的程式碼分析。 您可以停用的功能有一些限制，而關閉程式碼分析的程式會因幾個因素而有所不同：

- 專案類型（.NET Core/Standard 與 .NET Framework）

  .NET Core 和 .NET Standard 專案的 [程式碼分析] 屬性頁面上有選項，可讓您從安裝為 NuGet 套件的分析器關閉程式碼分析。 如需詳細資訊，請參閱[.Net Core 和 .NET Standard 專案](#net-core-and-net-standard-projects)。 若要關閉 .NET Framework 專案的原始碼分析，請參閱[.NET Framework 專案](#net-framework-projects)。

- NuGet 分析器套件與 VSIX 或內建分析器的比較

  目前，您無法停用內建分析器的即時程式碼分析，例如，規則識別碼 IDE0067。 同樣地，您無法針對已安裝為 Visual Studio 延伸模組（VSIX）一部分的分析器停用即時程式碼分析。 若要隱藏內建和 VSIX 式分析器的錯誤和警告，請選擇 [**分析** >  組建]，**並隱藏**功能表列上的 [作用中問題]。 您*可以*針對安裝為 NuGet 套件一部分的分析器，停用即時和建立時間分析。

- 來源分析與舊版分析

  本主題適用于原始碼分析，而不適用於舊版（二進位）分析。 如需停用舊版分析的詳細資訊，請參閱 [How to：啟用和停用舊版程式碼分析 @ no__t-0。

## <a name="net-core-and-net-standard-projects"></a>.NET Core 和 .NET Standard 專案

從 Visual Studio 2019 16.3 版開始，[程式碼分析] 屬性頁中有兩個核取方塊，可讓您控制以 NuGet 為基礎的分析器是否在組建時間和設計階段執行。 這些選項是專案特定的。

![啟用或停用即時程式碼分析，或在 Visual Studio 中的組建](media/run-on-build-run-live-analysis.png)

若要開啟此頁面，請以滑鼠右鍵按一下**方案總管**中的專案節點，然後選取 [**屬性**]。 選取 [程式**代碼分析**] 索引標籤。

- 若要在組建階段停用來源分析，請取消核取 [**在組建上執行**] 選項。
- 若要停用即時來源分析，請取消核取 [**在即時分析執行**] 選項。

> [!NOTE]
> 內建和以 VSIX 為基礎的分析器會繼續提供程式碼的即時分析，即使未核取 [**在即時分析上執行**] 也一樣。 如果您想要隱藏這些分析器的錯誤和警告，請選擇 [**分析** >  組建]，**並隱藏**功能表列上的 [作用中問題]。

## <a name="net-framework-projects"></a>.NET Framework 專案

若要針對安裝為 NuGet 套件一部分的分析器關閉原始程式碼分析，請將下列一個或多個 MSBuild 屬性新增至[專案](../ide/solutions-and-projects-in-visual-studio.md#project-file)檔。

| MSBuild 屬性 | 描述 | 預設 |
| - | - | - |
| `RunAnalyzersDuringBuild` | 控制以 NuGet 為基礎的分析器是否在組建階段執行。 | `true` |
| `RunAnalyzersDuringLiveAnalysis` | 控制以 NuGet 為基礎的分析器在設計階段是否即時分析程式碼。 | `true` |
| `RunAnalyzers` | 在組建和設計階段停用以 NuGet 為基礎的分析器。 這個屬性的優先順序高於 `RunAnalyzersDuringBuild`，`RunAnalyzersDuringLiveAnalysis`。 | `true` |

例如：

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>來源分析

您無法在 Visual Studio 2017 中關閉[來源分析](roslyn-analyzers-overview.md)。 如果您想要從錯誤清單清除分析器錯誤，可以在功能表列上選擇 [**分析** > ] [**執行程式碼分析] 和 [隱藏**作用中問題]，以隱藏所有目前的違規。 如需詳細資訊，請參閱[隱藏違規](use-roslyn-analyzers.md#suppress-violations)。

從 Visual Studio 2019 16.3 版開始，您可以關閉以 NuGet 為基礎的原始碼分析。 請考慮升級至 Visual Studio 2019。

## <a name="legacy-analysis"></a>舊版分析

您可以在 [程式**代碼分析**屬性] 頁面上停用舊版的組建時間分析。 如需詳細資訊，請參閱[如何：啟用和停用舊版程式碼分析 @ no__t-0。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [隱藏違規](use-roslyn-analyzers.md#suppress-violations)
- [如何：啟用和停用舊版程式碼分析 @ no__t-0
