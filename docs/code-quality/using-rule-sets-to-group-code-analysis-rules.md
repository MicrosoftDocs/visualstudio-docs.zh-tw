---
title: 程式碼分析規則集
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bae627e08faed01ab0efc8e64373ff86ed5c877e
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548020"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則

當您在 Visual Studio 中設定程式碼分析時, 您可以從內建*規則集*清單中選擇。 規則集是一組程式碼分析規則, 用以識別目標問題和該專案的特定條件。 例如, 您可以套用一個規則集, 其設計目的是針對可公開使用的 Api 掃描程式碼。 您也可以套用包含所有可用規則的規則集。

您可以自訂規則集, 方法是新增或刪除規則, 或變更規則嚴重性, 以在**錯誤清單**中顯示為警告或錯誤。 自訂的規則集可以滿足您特定開發環境的需求。 當您自訂規則集時, 規則集編輯器會提供搜尋和篩選工具, 協助您處理常式。

規則集適用于[managed 程式碼分析](analyzer-rule-sets.md)、[舊版的 managed 程式碼分析](how-to-configure-code-analysis-for-a-managed-code-project.md), 以及[ C++程式碼分析](using-rule-sets-to-specify-the-cpp-rules-to-run.md)。

## <a name="rule-set-format"></a>規則集格式

規則集是以 XML 格式在 *. 規則*集檔案中指定。 由識別碼和*動作*組成的規則會依檔案中的分析器識別碼和命名空間分組。

*規則集*檔案的內容看起來類似下列 XML:

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
> 在圖形**規則集編輯器**中[編輯規則集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)比較容易, 就像手動一樣。

## <a name="specify-a-rule-set-for-a-project"></a>指定專案的規則集

專案的規則集是由 Visual Studio 專案檔中的**CodeAnalysisRuleSet**屬性所指定。 例如：

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)