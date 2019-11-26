---
title: FxCop 分析器規則集和 editorconfig 檔
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2cf385aaf24db2172a61ddbe7ecf77dcbe40f3c
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74537776"
---
# <a name="enable-a-category-of-rules"></a>啟用規則的類別

分析器套件可能包含預先定義的[EditorConfig](use-roslyn-analyzers.md#rule-severity)和[規則集](using-rule-sets-to-group-code-analysis-rules.md)檔案，可讓您快速且輕鬆地啟用一類規則，例如安全性或設計規則。 [CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet analyzer 套件包含兩個規則集（從版本2.6.2 開始）和 EditorConfig 檔案（從版本2.9.5 開始）。 藉由啟用特定分類的規則，您可以識別目標問題和特定條件。

> [!NOTE]
> 從 Visual Studio 2019 16.3 版開始，支援啟用分析器規則並使用 EditorConfig 檔設定其嚴重性。

FxCop 分析器 NuGet 套件包含預先定義的規則集和 EditorConfig 檔，適用于下列規則類別：

- 所有規則
- 資料流程
- 設計
- 文件
- 全球化
- 互通性
- 性
- 命名
- 效能
- 從 FxCop 移植
- 可靠性
- 安全性
- 使用方式

這些規則的每個類別都有一個 EditorConfig 或規則集檔案，可：

- 啟用類別中的所有規則（並停用所有其他規則）
- 使用每個規則的預設嚴重性和啟用設定（並停用所有其他規則）

> [!TIP]
> [所有規則] 類別具有其他 EditorConfig 或規則集檔案，可停用所有規則。 使用此檔案可快速清除專案中的任何分析器警告或錯誤。

> [!TIP]
> 如果您要從舊版的 "FxCop" 分析遷移至以 .NET Compiler Platform 為基礎的程式碼分析，EditorConfig 和規則集檔案可讓您繼續使用類似[先前所用的](rule-set-reference.md)規則設定。

## <a name="predefined-editorconfig-files"></a>預先定義的 EditorConfig 檔

CodeAnalysis FxCopAnalyzers 分析器套件的預先定義 EditorConfig 檔位於 *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<版本\>\editorconfig*目錄中。 例如，啟用所有安全性規則的 EditorConfig 檔案位於 *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<版本\>\editorconfig\SecurityRulesEnabled\\. EditorConfig*。

將選擇的 editorconfig 檔案複製到您專案的根目錄。

## <a name="predefined-rule-sets"></a>預先定義的規則集

CodeAnalysis. FxCopAnalyzers analyzer 套件的預先定義規則集檔案位於 *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<version\>\rulesets*目錄中。 例如，啟用所有安全性規則的規則集檔案位於 *% USERPROFILE%\\. nuget\packages\microsoft.codeanalysis.fxcopanalyzers\\\<版本\>\rulesets\SecurityRulesEnabled.ruleset*。

複製一或多個規則集，並將它們貼入包含 Visual Studio 專案的目錄中，或直接加入**方案總管**。

您也可以將[預先定義的規則集自訂](how-to-create-a-custom-rule-set.md)為您的喜好設定。 例如，您可以變更一或多個規則的嚴重性，讓違規在**錯誤清單**中顯示為錯誤或警告。

### <a name="set-the-active-rule-set"></a>設定作用中規則集

設定作用中規則集的程式稍有不同，視您是否有 .NET Core/NET Standard 專案或 .NET Framework 專案而定。

#### <a name="net-core"></a>.NET Core

若要將規則設定為在 .NET Core 或 .NET Standard 專案中進行分析的作用中規則集，請手動將**CodeAnalysisRuleSet**屬性新增至您的專案檔。 例如，下列程式碼片段會將 `HelloWorld.ruleset` 設定為使用中的規則集。

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>請參閱

- [分析器常見問題集](analyzers-faq.md)
- [.NET Compiler Platform 分析器概觀](roslyn-analyzers-overview.md)
- [安裝分析器](install-roslyn-analyzers.md)
- [設定分析器](use-roslyn-analyzers.md)
- [使用規則集分組程式碼分析規則](using-rule-sets-to-group-code-analysis-rules.md)
