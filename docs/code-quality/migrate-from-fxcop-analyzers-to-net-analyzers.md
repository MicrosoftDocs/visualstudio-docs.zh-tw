---
title: 從 FxCop 分析器移轉至 .NET 分析器
ms.custom: SEO-VS-2020
description: 瞭解如何從 FxCop 分析器遷移至 .NET 分析器
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798254"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>從 FxCop 分析器移轉至 .NET 分析器

.NET Compiler Platform ( "Roslyn" 的來源分析 ) 分析器會取代 managed 程式碼的 [舊版分析](code-analysis-for-managed-code-overview.md) 。 許多舊版分析 (FxCop) 規則已改寫為來源分析器。

在 Visual Studio 2019 16.8 和 .NET 5.0 之前，這些分析器會以 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的形式傳送。

從 Visual Studio 2019 16.8 和 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](/dotnet/fundamentals/code-analysis/overview)。 如果您不想要移至 .NET 5 + SDK，或您偏好以 NuGet 套件為基礎的模型，則 `Microsoft.CodeAnalysis.NetAnalyzers` [nuget 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)中也會提供分析器。 您可能偏好以套件為基礎的模型來進行隨選版本更新。

> [!NOTE]
> 第一方 .NET 分析器是目標平臺中立的。 也就是說，您的專案不需要以特定的 .NET 平臺為目標。 分析器適用于以和舊版 .NET 版本為目標的專案 `net5.0` ，例如 `netcoreapp` 、 `netstandard` 和 `net472` 。

## <a name="migration-steps"></a>移轉步驟

從版本開始 `3.3.2` ， `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 套件已淘汰。 請依照下列步驟將您的專案或解決方案遷移 `Microsoft.CodeAnalysis.FxCopAnalyzers` 至 .net 分析器：

1. 卸載 `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 套件

2. [啟用或安裝 .net 分析器](install-net-analyzers.md)。 請注意，您不需要變更專案的目標平臺。

3. 啟用其他規則：與 `Microsoft.CodeAnalysis.NetAnalyzers` 更保守的比較 `Microsoft.CodeAnalysis.FxCopAnalyzers` 。 不同于將 microsoft.codeanalysis.fxcopanalyzers 套件，它只有一些正確性規則，預設會 [啟用為組建警告](/dotnet/fundamentals/code-analysis/overview#enabled-rules)。 您可以藉由自訂[AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild 屬性來[啟用其他規則](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules)。 例如，將屬性設定為， `AllEnabledByDefault` 預設會啟用所有適用的 CA 規則作為組建警告。

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>另請參閱

- [原始碼分析與舊版分析](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [從舊版分析移轉至 .NET 分析器](migrate-from-legacy-analysis-to-net-analyzers.md)
- [啟用或安裝 .NET 分析器](install-net-analyzers.md)
- [.NET 分析器的常見問題](net-analyzers-faq.yml)
- [設定 .NET 分析器](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
