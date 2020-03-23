---
title: 關閉代碼分析
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431393"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>如何禁用託管代碼的原始程式碼分析

::: moniker range=">=vs-2019"

此頁面可説明您在 Visual Studio 中禁用代碼分析。 可以禁用的內容有限制，關閉代碼分析的過程因以下幾個因素而異：

- 專案類型（.NET 核心/標準與 .NET 框架）

  .NET Core 和 .NET 標準專案在其代碼分析屬性頁上具有選項，允許您關閉作為 NuGet 包安裝的分析器的代碼分析。 有關詳細資訊，請參閱[.NET 核心和 .NET 標準專案](#net-core-and-net-standard-projects)。 要關閉 .NET 框架專案的原始程式碼分析，請參閱[.NET 框架專案](#net-framework-projects)。

- 源分析與舊分析

  本主題適用于原始程式碼分析，不適用於遺留（二進位）分析。 有關禁用舊版分析的資訊，請參閱[如何：啟用和禁用舊代碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

## <a name="net-core-and-net-standard-projects"></a>.NET 核心和 .NET 標準專案

從 Visual Studio 2019 版本 16.3 開始，代碼分析屬性頁中有兩個核取方塊，用於控制分析器在生成時間和設計階段是否運行。 這些選項特定于專案。

![在視覺化工作室中啟用或禁用即時代碼分析或構建](media/run-on-build-run-live-analysis.png)

要打開此頁面，請按右鍵**解決方案資源管理器**中的專案節點並選擇 **"屬性**"。 選擇 **"代碼分析**"選項卡。

- 要在生成時禁用源分析，請取消選中 **"在生成時運行**"選項。
- 要禁用即時源分析，請取消選中 **"運行即時分析**"選項。

> [!NOTE]
> 從 Visual Studio 2019 版本 16.5 開始，如果您更喜歡按需代碼分析執行工作流，則可以在即時分析和/或生成期間禁用分析器執行，並在專案或解決方案上按需手動觸發代碼分析一次。 有關手動運行代碼分析的資訊，請參閱[如何：手動運行託管代碼的代碼分析](how-to-run-code-analysis-manually-for-managed-code.md)。  

## <a name="net-framework-projects"></a>.NET 框架專案

要關閉分析器的原始程式碼分析，請向[專案檔案](../ide/solutions-and-projects-in-visual-studio.md#project-file)添加以下一個或多個 MSBuild 屬性。

| MSBuild 屬性 | 描述 | 預設 |
| - | - | - |
| `RunAnalyzersDuringBuild` | 控制分析器是否在生成時運行。 | `true` |
| `RunAnalyzersDuringLiveAnalysis` | 控制分析器是否在設計時即時分析代碼。 | `true` |
| `RunAnalyzers` | 在生成和設計階段禁用分析器。 此屬性優先于`RunAnalyzersDuringBuild`和`RunAnalyzersDuringLiveAnalysis`。 | `true` |

範例：

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>來源分析

您不能在 Visual Studio 2017 中關閉[源分析](roslyn-analyzers-overview.md)。 如果要從錯誤清單中清除分析器錯誤，可以通過選擇功能表列上的 **"分析** > **運行代碼分析"和"禁止活動問題"** 來抑制所有當前衝突。 有關詳細資訊，請參閱[禁止衝突](use-roslyn-analyzers.md#suppress-violations)。

從 Visual Studio 2019 版本 16.3 開始，您可以關閉原始程式碼分析或按需執行。 考慮升級到視覺工作室 2019。

## <a name="legacy-analysis"></a>舊版分析

您可以在 **"代碼分析"** 屬性頁上禁用舊版本時分析。 有關詳細資訊，請參閱[如何：啟用和禁用舊代碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [抑制違規行為](use-roslyn-analyzers.md#suppress-violations)
- [如何：啟用和禁用舊代碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
