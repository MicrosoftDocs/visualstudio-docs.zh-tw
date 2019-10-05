---
title: FxCop 分析器規則集
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974699"
---
# <a name="rule-sets-for-analyzer-packages"></a>分析器套件的規則集

預先定義的規則集包含在一些 NuGet 分析器套件中。 例如， [CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 封裝（從版本2.6.2 開始）中所包含的規則集會根據其類別來啟用或停用規則，例如安全性、命名或效能。 使用規則集可讓您輕鬆快速地只查看與特定規則分類相關的規則違規。

規則集是一組程式碼分析規則，可識別目標問題和特定條件。 規則集可讓您啟用或停用規則，並設定個別規則違規的嚴重性。 FxCop 分析器 NuGet 套件包含下列規則類別的預先定義規則集：

- 設計
- 文件
- 維護性維護性
- 命名
- 效能
- 可靠性
- 安全性
- 用法

如果您要從舊版的 "FxCop" 分析遷移至以 .NET Compiler Platform 為基礎的程式碼分析，這些規則集可讓您繼續使用類似[先前所用的](rule-set-reference.md)規則設定。

## <a name="use-analyzer-package-rule-sets"></a>流量分析器套件規則集

[安裝 NuGet 分析器套件](install-roslyn-analyzers.md)之後，請在其*規則*集目錄中找出預先定義的規則集。 例如，如果您參考了 `Microsoft.CodeAnalysis.FxCopAnalyzers` 分析器套件，則可以在% USERPROFILE% \\ 找到其*規則集*目錄 *。 nuget\packages\microsoft.codeanalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*。 從該處複製一或多個規則集，並將它們貼入包含 Visual Studio 專案的目錄中，或直接加入**方案總管**。

您也可以將[預先定義的規則集自訂](how-to-create-a-custom-rule-set.md)為您的喜好設定。 例如，您可以變更一或多個規則的嚴重性，讓違規在**錯誤清單**中顯示為錯誤或警告。

## <a name="set-the-active-rule-set"></a>設定作用中規則集

設定作用中規則集的程式稍有不同，視您是否有 .NET Core/NET Standard 專案或 .NET Framework 專案而定。

### <a name="net-core"></a>.NET Core

若要將規則設定為在 .NET Core 或 .NET Standard 專案中進行分析的作用中規則集，請手動將**CodeAnalysisRuleSet**屬性新增至您的專案檔。 例如，下列程式碼片段會將 `HelloWorld.ruleset` 設定為使用中的規則集。

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

若要將規則設定為在 .NET Framework 專案中進行分析的作用中規則集：

- 以滑鼠右鍵按一下**方案總管**中的專案，然後選擇 [**屬性**]。

- 在專案屬性頁中，選取 [程式**代碼分析**] 索引標籤。

::: moniker range="vs-2017"

- 在 [**執行此規則集**] 底下，選取 **[流覽]** ，然後選取您要複製到專案目錄中的所需規則集。

::: moniker-end

::: moniker range=">=vs-2019"

- 在 [作用中**規則**] 底下，選取 **[流覽]** ，然後選取您要複製到專案目錄中的所需規則集。

::: moniker-end

   現在，您只會看到在選取的規則集內已啟用規則的規則違規。

## <a name="available-rule-sets"></a>可用的規則集

預先定義的分析器規則集會包含三個規則集，其會影響封裝 @ no__t-0one 中的所有規則，其中一個會停用全部，另一個則會接受每個規則的預設嚴重性和啟用設定：

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

此外，封裝中的每個規則類別都有兩個規則集，例如 [效能] 或 [安全性]。 一個規則集可啟用類別目錄的所有規則，而一個規則集接受類別目錄中每個規則的預設嚴重性和啟用設定。

[CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 套件包含下列類別的規則集：

- 設計
- 文件
- 維護性維護性
- 命名
- 效能
- 可靠性
- 安全性
- 用法

## <a name="see-also"></a>另請參閱

- [分析器常見問題集](analyzers-faq.md)
- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [安裝分析器](install-roslyn-analyzers.md)
- [設定分析器](use-roslyn-analyzers.md)
- [使用規則集分組程式碼分析規則](using-rule-sets-to-group-code-analysis-rules.md)
