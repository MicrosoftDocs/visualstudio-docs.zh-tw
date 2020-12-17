---
title: EditorConfig 與分析器
ms.date: 03/11/2019
description: 瞭解 Visual Studio 中以 .NET Compiler Platform 為基礎的程式碼分析。 查看有關 EditorConfig 檔案、規則集和其他主題的問題答案。
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48dcb2d01e53502c371595048666fd94c267b6ec
ms.sourcegitcommit: fed8782b2fb2ca18a90746b6e7e0b33f3fde10f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97646381"
---
# <a name="code-analysis-faq"></a>程式碼分析常見問題

此頁面包含 Visual Studio 中以 .NET Compiler Platform 為基礎的程式碼分析之一些常見問題的解答。

## <a name="code-analysis-versus-editorconfig"></a>程式碼分析與 EditorConfig

**問**：我是否應該使用程式碼分析或 EditorConfig 來檢查程式碼樣式？

**答**：程式碼分析和 EditorConfig 檔案的工作手邊。 當您 [在 EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options) 檔或 [文字編輯器](../ide/code-styles-and-code-cleanup.md) 的 [選項] 頁面上定義程式碼樣式時，實際上是設定 Visual Studio 內建的程式碼分析器。 您可以使用 EditorConfig 檔案來啟用或停用分析器規則，也可以設定 NuGet 分析器套件。

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig 與規則集的比較

**問**：我是否應該使用規則集或 EditorConfig 檔來設定我的分析器？

**答**：規則集和 EditorConfig 檔案可以並存，也可以用來設定分析器。 EditorConfig 檔案和規則集都可讓您啟用和停用規則，並設定其嚴重性。

不過，EditorConfig 檔也提供其他設定規則的方式：

- 針對 .NET 程式碼品質分析器，EditorConfig 檔可讓您 [定義要分析的程式碼類型](/dotnet/fundamentals/code-analysis/code-quality-rule-options)。
- 針對 Visual Studio 內建的 .NET 程式碼樣式分析器，EditorConfig 檔可讓您定義程式碼基底 [的慣用程式碼樣式](/dotnet/fundamentals/code-analysis/code-style-rule-options) 。

除了規則集和 EditorConfig 檔之外，某些分析器會透過使用標記為 c # 和 VB 編譯器之 [其他](../ide/build-actions.md#build-action-values) 檔案的文字檔來設定。

> [!NOTE]
> - EditorConfig 檔案只能用來啟用規則，並在 Visual Studio 2019 16.3 版和更新版本中設定其嚴重性。
> - EditorConfig 檔案不能用來設定舊版分析，而規則集可以。

## <a name="code-analysis-in-ci-builds"></a>CI 組建中的程式碼分析

**問**：以 .NET Compiler Platform 為基礎的程式碼分析是否適用于 (CI) 組建的持續整合？

**答**：是。 針對從 NuGet 套件安裝的分析器，系統會 [在組建階段強制執行](roslyn-analyzers-overview.md#build-errors)這些規則，包括在 CI 組建期間。 CI 組建中使用的分析器會根據規則集和 EditorConfig 檔來設定規則。 目前，Visual Studio 內建的程式碼分析器未以 NuGet 套件的形式提供，因此不會在 CI 組建中強制執行這些規則。

## <a name="ide-analyzers-versus-stylecop"></a>IDE 分析器與 StyleCop

**問**： Visual Studio IDE 程式碼分析器與 StyleCop 分析器之間有何差異？

**答**： Visual Studio IDE 包含內建分析器，可同時尋找程式碼樣式和品質問題。 這些規則可協助您在推出新的語言功能時使用它們，並改善程式碼的可維護性。 IDE 分析器會隨著每個 Visual Studio 版本持續更新。

[StyleCop 分析器](https://github.com/DotNetAnalyzers/StyleCopAnalyzers) 是以 NuGet 套件形式安裝的協力廠商分析器，可檢查您程式碼中的樣式一致性。 一般而言，StyleCop 規則可讓您設定程式碼基底的個人喜好設定，而不會對另一個樣式進行建議。

## <a name="code-analyzers-versus-legacy-analysis"></a>程式碼分析器與舊版分析

**問**：舊版分析和以 .NET Compiler Platform 為基礎的程式碼分析有何差異？

**答**：以 .NET Compiler Platform 為基礎的程式碼分析會即時分析原始程式碼和編譯期間，而舊版分析會在組建完成後分析二進位檔案。 如需詳細資訊，請參閱以 [.NET Compiler Platform 為基礎的分析與舊版分析](../code-quality/net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)。

## <a name="fxcop-analyzers-versus-net-analyzers"></a>FxCop 分析器與 .NET 分析器的比較

**問**： FxCop 分析器和 .Net 分析器有何不同？

**答**： fxcop 分析器和 .Net 分析器都會參考 fxcop CA 規則 ) 分析器的 .NET Compiler Platform ( "Roslyn"。 在 Visual Studio 2019 16.8 和 .NET 5.0 之前，這些分析器會以 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)的形式傳送。 從 Visual Studio 2019 16.8 和 .NET 5.0 開始，這些分析器會 [隨附于 .NET SDK](/dotnet/fundamentals/code-analysis/overview)。 它們也可以作為 `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)。 請考慮 [從 FxCop 分析器遷移至 .net 分析器](migrate-from-fxcop-analyzers-to-net-analyzers.md)。

## <a name="treat-warnings-as-errors"></a>將警告視為錯誤

**問**：我的專案使用 build 選項將警告視為錯誤。 從舊版分析遷移至原始程式碼分析之後，所有程式碼分析警告現在都會顯示為錯誤。 我該如何避免？

**答**：若要防止程式碼分析警告被視為錯誤，請遵循下列步驟：

  1. 使用下列內容建立 .props 檔案：

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. 將程式程式碼新增至 .csproj 或 vbproj 專案檔，以匯入您在上一個步驟中建立的 .props 檔案。 這一行必須放在匯入 .props 檔案的任何行之前。 例如，如果您的 .props 檔案命名為 codeanalysis. .props：

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.NetAnalyzers.5.0.0\build\Microsoft.CodeAnalysis.NetAnalyzers.props')" />
     ...
     ```

## <a name="code-analysis-solution-property-page"></a>程式碼分析解決方案屬性頁面

**問**：解決方案的 [程式碼分析] 屬性頁在哪裡？

**答**：已移除方案層級的 [程式碼分析] 屬性頁，以改用更可靠的共用屬性群組。 若要在專案層級管理程式碼分析，仍可使用 [程式碼分析] 屬性頁。 針對 managed 專案 (，我們也建議將規則設定從規則集遷移至 EditorConfig。 ) 若要在方案或存放庫中跨多個/所有專案共用規則集，建議您在共用的 .props/目標檔案或 *目錄 .props/目錄 .targets* 檔案中定義具有 [CodeAnalysisRuleSet](../code-quality/using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project)屬性的屬性群組。 如果您沒有任何專案匯入的一般 .props 或目標，則應該考慮將這類屬性群組加入 .props 或頂層方案目錄的 [目錄 .targets](../msbuild/customize-your-build.md) 檔案，此檔案會自動匯入至目錄或其子目錄中定義的所有專案檔。

## <a name="see-also"></a>另請參閱

- [分析器總覽](roslyn-analyzers-overview.md)
- [EditorConfig 的 .NET 編碼慣例設定](/dotnet/fundamentals/code-analysis/code-style-rule-options)