---
title: 編輯器配置與分析器
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 680d52ff04553d399b6abeb53919d8aafd4fa792
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301689"
---
# <a name="code-analysis-faq"></a>代碼分析常見問題解答

此頁包含有關 Visual Studio 中有關 .NET 編譯器平臺代碼分析的一些常見問題的解答。

## <a name="code-analysis-versus-editorconfig"></a>代碼分析與編輯器配置

**問**：我應該使用代碼分析或編輯器配置來檢查代碼樣式嗎？

**A**： 代碼分析和編輯器分析檔是手牽手工作的。 當您[在 EditorConfig 檔](../ide/editorconfig-code-style-settings-reference.md)或[文字編輯器選項](../ide/code-styles-and-code-cleanup.md)頁上定義代碼樣式時，實際上是在配置視覺化工作室中內置的代碼分析器。 編輯器設定檔可用於啟用或禁用分析器規則，以及配置一些 NuGet 分析器包，如[FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="editorconfig-versus-rule-sets"></a>編輯器配置與規則集

**問**：我是否應該使用規則集或編輯器設定檔配置分析器？

**A**： 規則集和編輯器設定檔可以共存，並且都可用於配置分析器。 編輯器設定檔和規則集都允許您啟用和禁用規則並設置其嚴重性。

但是，EditorConfig 檔提供了配置規則的其他方法：

- 對於 FxCop 分析器，EditorConfig 檔允許您[定義要分析的代碼類型](fxcop-analyzer-options.md)。
- 對於內置於 Visual Studio 中的代碼樣式分析器，Editor Config 檔允許您為代碼庫[定義首選的代碼樣式](../ide/editorconfig-code-style-settings-reference.md)。

除了規則集和 EditorConfig 檔之外，某些分析器還通過使用標記為 C# 和 VB 編譯器[的其他檔](../ide/build-actions.md#build-action-values)的文字檔進行配置。

> [!NOTE]
> - EditorConfig 檔只能在 Visual Studio 2019 版本 16.3 及更高版本中啟用規則並設置其嚴重性。
> - 編輯器設定檔不能用於配置舊版分析，而規則集可以。

## <a name="code-analysis-in-ci-builds"></a>CI 生成中的代碼分析

**問**：基於 .NET 編譯器平臺的代碼分析在持續集成 （CI） 生成中是否正常工作？

**答**：是的。 對於從 NuGet 包安裝的分析器，這些規則在[生成時（](roslyn-analyzers-overview.md#build-errors)包括在 CI 生成期間）強制執行。 CI 中使用的分析器從規則集和編輯器設定檔生成尊重規則配置。 目前，Visual Studio 中內置的代碼分析器不能作為 NuGet 包提供，因此這些規則在 CI 生成中無法執行。

## <a name="ide-analyzers-versus-stylecop"></a>IDE 分析儀與 StyleCop

**問**：Visual Studio IDE 代碼分析器和 StyleCop 分析器之間的區別是什麼？

**答**： Visual Studio IDE 包括內置分析器，可同時查找代碼樣式和品質問題。 這些規則可説明您在引入新語言功能時使用這些功能，並提高代碼的可維護性。 IDE 分析器會隨每個視覺化工作室版本不斷更新。

[StyleCop 分析器](https://github.com/DotNetAnalyzers/StyleCopAnalyzers)是作為 NuGet 包安裝的協力廠商分析器，用於檢查代碼中的樣式一致性。 通常，StyleCop 規則允許您為代碼庫設置個人首選項，而無需將一種樣式推薦到另一種樣式。

## <a name="code-analyzers-versus-legacy-analysis"></a>代碼分析器與舊分析

**問**：舊版分析和基於 .NET 編譯器平臺的代碼分析有何區別？

**A**： .NET 編譯器平臺代碼分析即時和編譯期間分析原始程式碼，而舊分析在生成完成後分析二進位檔案。 有關詳細資訊，請參閱[.NET 編譯器平臺分析與舊分析和](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) [FxCop 分析器常見問題解答](fxcop-analyzers-faq.md)。

## <a name="treat-warnings-as-errors"></a>將警告視為錯誤

**問**：我的專案使用生成選項將警告視為錯誤。 從舊分析遷移到原始程式碼分析後，所有代碼分析警告現在都顯示為錯誤。 我怎樣才能防止這種情況？

**為**防止代碼分析警告被視為錯誤，請按照以下步驟操作：

  1. 創建包含以下內容的 .props 檔：

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. 向 .csproj 或 .vbproj 專案檔案添加行以導入您在上一步中創建的 .props 檔。 此行必須放置在導入 FxCop 分析器 .props 檔的任何行之前。 例如，如果您的 .props 檔案名為代碼分析.props：

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>另請參閱

- [分析儀概述](roslyn-analyzers-overview.md)
- [.NET 編碼約定設置，用於編輯器配置](../ide/editorconfig-code-style-settings-reference.md)
