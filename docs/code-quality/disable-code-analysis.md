---
title: 關閉程式碼分析
ms.date: 09/01/2020
description: 瞭解如何在 .NET Core、.NET Standard 和 .NET Framework 專案中關閉 Visual Studio 的原始程式碼分析。
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.openlocfilehash: 6a1f1466caa921d46ce4701f5074b98f3d5ba051
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860382"
---
# <a name="disable-source-code-analysis-for-net"></a>停用 .NET 的原始程式碼分析

::: moniker range=">=vs-2019"

此頁面可協助您停用 Visual Studio 中的程式碼分析。 您可以停用的功能有一些限制，而關閉程式碼分析的程式則會根據幾個因素而有所不同：

- 專案類型 ( .NET Core/Standard 與 .NET Framework) 

  .NET Core 和 .NET Standard 專案的 [程式碼分析] 屬性頁面上有選項，可讓您從安裝為 NuGet 套件的分析器關閉程式碼分析。 如需詳細資訊，請參閱 [.Net Core 和 .NET Standard 專案](#net-core-and-net-standard-projects)。 若要關閉 .NET Framework 專案的原始程式碼分析，請參閱 [.NET Framework 專案](#net-framework-projects)。

- 來源分析與舊版分析

  本主題適用于原始程式碼分析，而不是舊版 (二進位) 分析。 如需停用舊版分析的詳細資訊，請參閱 [如何：啟用和停用舊版程式碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

## <a name="net-core-and-net-standard-projects"></a>.NET Core 和 .NET Standard 專案

從 Visual Studio 2019 版本16.3 開始，[程式碼分析] 屬性頁中有兩個可用的核取方塊，可讓您控制分析器是否要在組建階段和設計階段執行。 這些選項是專案特定的。

![啟用或停用即時程式碼分析或 Visual Studio 中的組建](media/run-on-build-run-live-analysis.png)

若要開啟此頁面，請在 **方案總管** 中的專案節點上按一下滑鼠右鍵，然後選取 [ **屬性**]。 選取 [程式 **代碼分析** ] 索引標籤。

- 若要在組建階段停用來源分析，請取消核取 [ **在組建上執行** ] 選項。
- 若要停用即時來源分析，請取消核取 [ **在即時分析上執行** ] 選項。

> [!NOTE]
> 從 Visual Studio 2019 16.5 版開始，如果您偏好隨選程式碼分析執行工作流程，您可以在即時分析和/或組建期間停用分析器執行，並視需要在專案或解決方案上手動觸發程式碼分析。 如需手動執行程式碼分析的詳細資訊，請參閱 [如何：針對 Managed 程式碼手動執行程式碼分析](how-to-run-code-analysis-manually-for-managed-code.md)。

## <a name="net-framework-projects"></a>.NET Framework 專案

若要關閉分析器的原始程式碼分析，請在 [專案](../ide/solutions-and-projects-in-visual-studio.md#project-file)檔中加入下列一或多個 MSBuild 屬性。

| MSBuild 屬性 | 描述 | 預設 |
| - | - | - |
| `RunAnalyzersDuringBuild` | 控制分析器是否在組建階段執行。 | `true` |
| `RunAnalyzersDuringLiveAnalysis` | 控制分析器是否要在設計階段即時分析程式碼。 | `true` |
| `RunAnalyzers` | 在組建和設計階段停用分析器。 這個屬性優先于 `RunAnalyzersDuringBuild` 和 `RunAnalyzersDuringLiveAnalysis` 。 | `true` |

範例：

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>來源分析

您無法在 Visual Studio 2017 中關閉 [來源分析](roslyn-analyzers-overview.md) 。 如果您想要從 [**錯誤清單**] 中清除分析器錯誤，您可以選取 [**分析**  >  **執行程式碼分析]，並隱藏** 功能表列上的 [作用中問題]，以隱藏所有目前的違規。 如需詳細資訊，請參閱 [隱藏違規](use-roslyn-analyzers.md#suppress-violations)。

從 Visual Studio 2019 版本16.3 開始，您可以關閉原始碼分析，或視需要執行。 請考慮升級至 Visual Studio 2019。

## <a name="legacy-analysis"></a>舊版分析

您可以在 [程式 **代碼分析** ] 屬性頁上停用舊版的組建時間分析。 如需詳細資訊，請參閱 [如何：啟用和停用舊版程式碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

::: moniker-end

## <a name="see-also"></a>另請參閱

- [隱藏違規](use-roslyn-analyzers.md#suppress-violations)
- [如何：啟用和停用舊版程式碼分析](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
