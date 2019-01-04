---
title: 分析器規則集
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 514f264186047c044e5db1b944cd62d517588e80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885219"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Roslyn 分析器的規則集

預先定義的規則集都包含一些 NuGet 分析器套件。 例如，規則集隨附[Microsoft.CodeAnalysis.FxCopAnalyzers NuGet 分析器套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)（從版本 2.6.2） 啟用或停用規則，根據其類別，例如安全性、 命名，或效能。 使用規則集可讓您輕鬆快速地查看 屬於特定分類規則的規則違規。

如果您要從舊版的 「 FxCop 「 靜態程式碼分析中移轉至 Roslyn 分析器，這些規則集可讓您繼續使用您先前使用的相同規則組態。

## <a name="use-analyzer-rule-sets"></a>使用分析器規則集

之後您[安裝 nuget 分析器](install-roslyn-analyzers.md)，找出預先定義的規則中設定其*ruleset*目錄，例如 *%USERPROFILE%\\.nuget\packages\microsoft.codequality.analyzers\<版本 > \rulesets*。 從該處，您可以拖放，或複製並貼上，一或多個規則集至您的 Visual Studio 專案中**方案總管 中**。

若要讓規則集的作用中的規則集分析，以滑鼠右鍵按一下專案中**方案總管**，然後選擇**屬性**。 在 專案屬性頁中，選取**程式碼分析** 索引標籤。底下**執行此規則集**，選取**瀏覽**，然後選取 複製到專案目錄中您所需的規則集。 現在您只看到 vybranou 的 sadu pravidel 中啟用這些規則的規則違規。

您也可以[來自訂預先定義的規則集](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set)為您的喜好設定。 比方說，變更一或多個規則的嚴重性，以便顯示為錯誤或警告的違規**錯誤清單**。

## <a name="available-rule-sets"></a>可用的規則集

預先定義的分析器規則集包含三個會影響封裝中的所有規則的 ruleset&mdash;分別，可讓它們全部、 停用，和一個接受每個規則的預設的嚴重性和啟用設定：

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

此外，還有每個規則，在封裝中，例如效能或安全性類別的兩個規則集。 一個規則集可讓類別的所有規則和一個規則集，會接受 「 類別目錄中的每個規則的預設嚴重性和啟用設定。

 [Microsoft.CodeAnalysis.FxCopAnalyzers NuGet 分析器套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)包含下列類別，以符合適用於舊版的 「 FxCop 「 靜態程式碼分析規則集的規則集：

- 設計
- 文件
- 維護性維護性
- 命名
- 效能
- 可靠性
- 安全性
- 用法

## <a name="see-also"></a>另請參閱

- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [安裝.NET Compiler Platform 分析器](install-roslyn-analyzers.md)
- [設定和使用 Roslyn 分析器規則](use-roslyn-analyzers.md)
- [使用規則集分組程式碼分析規則](using-rule-sets-to-group-code-analysis-rules.md)