---
title: 從 FxCop 分析器遷移至 .NET 分析器
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112215"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>從 FxCop 分析器遷移至 .NET 分析器

.NET Compiler Platform ( "Roslyn" 的來源分析 ) 分析器會取代 managed 程式碼的 [舊版分析](code-analysis-for-managed-code-overview.md) 。 許多舊版分析 (FxCop) 規則已改寫為來源分析器。

在 Visual Studio 2019 16.8 和 .NET 5.0 之前，這些分析器會以 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的形式傳送。

從 Visual Studio 2019 16.8 和 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](/dotnet/fundamentals/code-analysis/overview)。 它們也可以作為 `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)。 `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 套件即將淘汰。

## <a name="migration-steps"></a>移轉步驟

請依照下列步驟將您的專案或解決方案遷移 `Microsoft.CodeAnalysis.FxCopAnalyzers` 至 .net 分析器：

1. 卸載 `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 套件

2. [啟用或安裝 .NET 分析器](install-net-analyzers.md)

3. 啟用其他規則：與 `Microsoft.CodeAnalysis.NetAnalyzers` 更保守的比較 `Microsoft.CodeAnalysis.FxCopAnalyzers` 。 不同于將 microsoft.codeanalysis.fxcopanalyzers 套件，它只有一些正確性規則，預設會 [啟用為組建警告](/dotnet/fundamentals/code-analysis/overview#enabled-rules)。 您可以藉由自訂[AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild 屬性來[啟用其他規則](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules)。 例如，將屬性設定為， `AllEnabledByDefault` 預設會啟用所有適用的 CA 規則作為組建警告。

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>另請參閱

- [原始碼分析與舊版分析](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [從舊版分析遷移至 .NET 分析器](migrate-from-legacy-analysis-to-net-analyzers.md)
- [啟用或安裝 .NET 分析器](install-net-analyzers.md)
- [.NET 分析器的常見問題](net-analyzers-faq.md)
- [設定 .NET 分析器](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
