---
title: 編輯器設定與分析器
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56b0c0defe5593c9dc0e2111ef5984a5c51eaf55
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760128"
---
# <a name="code-analysis-faq"></a>程式碼分析常見問題解答

此頁包含有關 Visual Studio 中有關 .NET 編譯器平台代碼分析的一些常見問題的解答。

## <a name="code-analysis-versus-editorconfig"></a>程式碼分析與編輯器設定

**問**:我應該使用代碼分析或編輯器配置來檢查代碼樣式嗎?

**A:** 程式碼分析和編輯器分析檔是手牽手工作的。 當您[在 EditorConfig 檔](../ide/editorconfig-code-style-settings-reference.md)或[文字編輯器選項](../ide/code-styles-and-code-cleanup.md)頁上定義代碼樣式時,實際上是在配置可視化工作室中內置的代碼分析器。 編輯器設定檔可用於啟用或關閉分析器規則,以及設定一些 NuGet 分析器套件,如[FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="editorconfig-versus-rule-sets"></a>編輯器設定與規則集

**問**:我是否應該使用規則集或編輯器設定檔配置分析器?

**A:** 規則集和編輯器設定檔可以共存,並且都可用於配置分析器。 編輯器設定檔和規則集都允許您啟用和禁用規則並設定其嚴重性。

但是,EditorConfig 檔提供設定規則的其他方法:

- 對於 FxCop 分析器,EditorConfig 檔案允許您[定義要分析的代碼類型](fxcop-analyzer-options.md)。
- 對文字庫定義的[代碼樣式](../ide/editorconfig-code-style-settings-reference.md)。

除了規則集和 EditorConfig 檔之外,某些分析器還透過使用標記為 C# 和 VB 編譯器[的其他檔案](../ide/build-actions.md#build-action-values)的文本檔進行配置。

> [!NOTE]
> - EditorConfig 檔只能在 Visual Studio 2019 版本 16.3 及更高版本中啟用規則並設置其嚴重性。
> - 編輯器設定檔不能用於配置舊版分析,而規則集可以。

## <a name="code-analysis-in-ci-builds"></a>CI 產生的代碼分析

**問**:基於 .NET 編譯器平台的代碼分析在持續整合 (CI) 產生中是否正常工作?

**答**:是的。 對於從 NuGet 包安裝的分析器,這些規則在[生成時(](roslyn-analyzers-overview.md#build-errors)包括在 CI 生成期間)強制執行。 CI 中使用的分析器從規則集和編輯器設定檔生成尊重規則配置。 目前,Visual Studio 中內置的代碼分析器不能作為 NuGet 包提供,因此這些規則在 CI 生成中不可執行。

## <a name="ide-analyzers-versus-stylecop"></a>IDE 分析儀與 StyleCop

**問**:Visual Studio IDE 代碼分析器和 StyleCop 分析器之間的區別是什麼?

**答**: Visual Studio IDE 包括內建分析器,可同時查找代碼樣式和質量問題。 這些規則可説明您在引入新語言功能時使用這些功能,並提高代碼的可維護性。 IDE 分析器會隨每個可視化工作室版本不斷更新。

[StyleCop 分析器](https://github.com/DotNetAnalyzers/StyleCopAnalyzers)是作為 NuGet 套件安裝的第三方分析器,用於檢查代碼中的樣式一致性。 通常,StyleCop 規則允許您為代碼庫設置個人首選項,而無需將一種樣式推薦到另一種樣式。

## <a name="code-analyzers-versus-legacy-analysis"></a>程式碼分析器與舊分析

**問**:舊版分析和基於 .NET 編譯器平臺的代碼分析有何區別?

**A**: .NET 編譯器平台代碼分析即時和編譯期間分析原始程式碼,而舊分析在生成完成後分析二進位檔案。 有關詳細資訊,請參閱[.NET 編譯器平臺分析與舊分析和](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis) [FxCop 分析器常見問題解答](fxcop-analyzers-faq.md)。

## <a name="treat-warnings-as-errors"></a>將警告視為錯誤

**問**:我的專案使用生成選項將警告視為錯誤。 從舊分析遷移到原始碼分析後,所有代碼分析警告現在都顯示為錯誤。 我怎樣才能防止這種情況?

**為**防止代碼分析警告被視爲錯誤,請按照以下步驟操作:

  1. 建立包含以下內容的 .props 檔案:

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. 加入 .csproj 或 .vbproj 專案檔加入行以匯入您在上一步中建立的 .props 檔案。 此行必須放置在導入FxCop分析器 .props檔的任何行之前。 例如,如果您的 .props 檔案名為代碼分析.props:

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>程式碼分析解決方案屬性頁

**問**:解決方案的代碼分析屬性頁在哪裡?

**A:** 解決方案等級的代碼分析屬性頁被刪除,有利於更可靠的共用屬性組。 要在項目級別管理代碼分析,代碼分析屬性頁仍然可用。 (對於託管項目,我們還建議從規則集遷移到編輯器配置,以便進行規則配置。 對於在解決方案或回購中的多個/所有專案中共用規則集,我們建議在共用道具/目標檔或 Directory.props/Directory.target 檔中使用 CodeAnalysisRuleSet 屬性定義屬性組。 如果您沒有任何這樣的常見道具或目標,您的專案匯入,應考慮[將這樣的屬性組添加到目錄.props 或 Directory.target 在頂級解決方案目錄中,該目錄會自動匯入目錄或其子目錄中定義的所有專案檔中](https://docs.microsoft.com/visualstudio/msbuild/customize-your-build?directorybuildprops-and-directorybuildtargets)。

## <a name="see-also"></a>另請參閱

- [分析儀概述](roslyn-analyzers-overview.md)
- [.NET 編碼約定設定,用於編輯器配置](../ide/editorconfig-code-style-settings-reference.md)
