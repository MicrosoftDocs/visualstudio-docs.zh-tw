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
ms.openlocfilehash: 701b178ea161884ef748008b1f933a53fc35a1cb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914470"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>使用規則集分組程式碼分析規則

當您在 Visual Studio 中設定程式碼分析時，您可以從內建清單中選擇*規則集*。 規則集適用於專案，而且是一組的程式碼分析規則，識別目標的問題，以及該專案的特定條件。 比方說，您可以將套用的規則集是設計用來公開可用的 Api，掃描程式碼，或只是最小建議規則。 您也可以套用的規則集包含所有規則。

您可以自訂規則集顯示為警告或錯誤中的新增或刪除規則，或變更規則嚴重性**錯誤清單**。 自訂的規則集可滿足您特定的開發環境的需求。 當您自訂規則集時，規則集編輯器會提供搜尋和篩選工具，可協助您在程序。

規則集可供[的 managed 程式碼靜態分析](how-to-configure-code-analysis-for-a-managed-code-project.md)， [c + + 程式碼分析](using-rule-sets-to-specify-the-cpp-rules-to-run.md)，並[Roslyn 分析器](analyzer-rule-sets.md)。

## <a name="rule-set-format"></a>規則集格式

中的 XML 格式中指定的規則集 *.ruleset*檔案。 包含識別碼的規則和*動作*，依據分析器 ID 和檔案中的命名空間。

內容 *.ruleset*檔案看起來類似此 XML:

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
> 更輕鬆地[編輯規則集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)中的圖形**規則集編輯器**比以手動方式。

## <a name="specify-a-rule-set-for-a-project"></a>指定的規則集的專案

規則集的專案由**CodeAnalysisRuleSet** Visual Studio 專案檔中的屬性。 例如: 

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>另請參閱

- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)