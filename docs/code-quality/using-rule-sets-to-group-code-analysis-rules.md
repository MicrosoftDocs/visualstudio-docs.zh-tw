---
title: 程式碼分析規則集
ms.date: 04/02/2018
description: 瞭解 Visual Studio 程式碼分析中的內建和自訂規則集。 瞭解如何在檔案中指定規則集，以及如何在專案中設定規則集。
ms.custom: SEO-VS-2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 980c77067ac237dba13c8c888c358a0adeab6d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859654"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>使用規則集將程式碼分析規則分組

當您在 Visual Studio 中設定程式碼分析時，可以從內建 *規則集* 的清單中選擇。 規則集是一組程式碼分析規則，可識別該專案的目標問題和特定條件。 例如，您可以套用設計來掃描程式碼的規則集，以取得公開可用的 Api。 您也可以套用包含所有可用規則的規則集。

您可以藉由新增或刪除規則來自訂規則集，或將規則嚴重性變更為在 **錯誤清單** 中顯示為警告或錯誤。 自訂規則集可以滿足您特定開發環境的需求。 當您自訂規則集時，規則集編輯器會提供搜尋和篩選工具來協助您進行處理。

規則集適用于 [managed 程式碼分析](/dotnet/fundamentals/code-analysis/code-quality-rule-options)、 [managed 程式碼的舊版分析](how-to-configure-code-analysis-for-a-managed-code-project.md)，以及 [c + + 程式碼分析](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)。

## <a name="rule-set-format"></a>規則集格式

規則集是以 XML 格式在 *. 規則* 集檔案中指定。 由識別碼和 *動作* 組成的規則會依分析器識別碼和檔案中的命名空間來分組。

*規則集* 檔案的內容看起來類似以下 XML：

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> 您可以更輕鬆地在圖形 **規則集編輯器** 中 [編輯規則集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)（而不是手動）。

## <a name="specify-a-rule-set-for-a-project"></a>指定專案的規則集

專案的規則集是由 Visual Studio 專案檔中的 **CodeAnalysisRuleSet** 屬性所指定。 例如：

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)