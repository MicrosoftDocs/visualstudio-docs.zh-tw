---
title: EditorConfig 與分析器的比較
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12e6681490c6c933369d3fef064ec88f240e3a99
ms.sourcegitcommit: b23d73c86ec7720c4cd9a58050860bc559623a3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72172765"
---
# <a name="code-analysis-faq"></a>程式碼分析常見問題

此頁面包含 Visual Studio 中以 .NET Compiler Platform 為基礎之程式碼分析的一些常見問題的解答。

## <a name="code-analysis-versus-editorconfig"></a>程式碼分析與 EditorConfig

**問**：我應該使用程式碼分析或 EditorConfig 來檢查程式碼樣式嗎？

**答**：程式碼分析和 EditorConfig 檔會手上工作。 當您[在 EditorConfig](../ide/editorconfig-code-style-settings-reference.md)檔或 [[文字編輯器] 選項](../ide/code-styles-and-code-cleanup.md)頁面上定義程式碼樣式時，實際上是設定 Visual Studio 內建的程式碼分析器。 EditorConfig 檔案可用來啟用或停用分析器規則，也可以設定一些 NuGet 分析器套件，例如[FxCop](configure-fxcop-analyzers.md)分析器。

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig 與規則集的比較

**問**：我應該使用規則集或 EditorConfig 檔來設定分析器嗎？

**答**：規則集和 EditorConfig 檔可以並存，而且可以用來設定分析器。 EditorConfig 檔案和規則集都可讓您啟用和停用規則，並設定其嚴重性。

不過，EditorConfig 檔案也提供其他方式來設定規則：

- 針對 FxCop 分析器，EditorConfig files 可讓您[定義要分析的程式碼類型](fxcop-analyzer-options.md)。
- 對於內建于 Visual Studio 的程式碼樣式分析器，EditorConfig 檔案可讓您定義程式碼基底[慣用的程式碼樣式](../ide/editorconfig-code-style-settings-reference.md)。

除了規則集和 EditorConfig 檔以外，有些分析器是透過使用標示為C#和 VB 編譯器之[其他](../ide/build-actions.md#build-action-values)檔案的文字檔來設定。

> [!NOTE]
> - EditorConfig 檔案只能用來啟用規則，並在 Visual Studio 2019 16.3 版和更新版本中設定其嚴重性。
> - EditorConfig 檔案無法用來設定舊版分析，而規則集可以。

## <a name="code-analysis-in-ci-builds"></a>CI 組建中的程式碼分析

**問**：以 .NET Compiler Platform 為基礎的程式碼分析在持續整合（CI）組建中運作嗎？

**答**：是的。 針對從 NuGet 封裝安裝的分析器，這些規則會[在組建階段強制執行](roslyn-analyzers-overview.md#build-errors)，包括在 CI 組建期間。 CI 組建中使用的分析器會遵循規則集和 EditorConfig 檔中的規則設定。 目前內建在 Visual Studio 中的程式碼分析器無法做為 NuGet 套件使用，因此這些規則無法在 CI 組建中強制執行。

## <a name="ide-analyzers-versus-stylecop"></a>IDE 分析器與 Stylecop 能夠的比較

**問**：Visual Studio IDE 程式碼分析器與 Stylecop 能夠分析器有何不同？

**答**：Visual Studio IDE 包含內建分析器，可同時尋找程式碼樣式和品質問題。 這些規則可協助您在引進新的語言功能時，使用它們，並改善程式碼的可維護性。 IDE 分析器會隨著每個 Visual Studio 版本持續更新。

[Stylecop 能夠分析器](https://github.com/DotNetAnalyzers/StyleCopAnalyzers)是以 NuGet 套件形式安裝的協力廠商分析器，可檢查程式碼中的樣式一致性。 一般來說，Stylecop 能夠規則可讓您設定程式碼基底的個人喜好設定，而不需要在另一個樣式上建議。

## <a name="code-analyzers-versus-legacy-analysis"></a>程式碼分析器與舊版分析

**問**：舊版分析和以 .NET Compiler Platform 為基礎的程式碼分析有何不同？

**答**：以 .NET Compiler Platform 為基礎的程式碼分析會即時分析原始程式碼和編譯期間，而舊版分析會在完成組建之後分析二進位檔案。 如需詳細資訊，請參閱以[.NET Compiler Platform 為基礎的分析與舊版分析](roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)和[FxCop 分析器常見問題](fxcop-analyzers-faq.md)。

## <a name="treat-warnings-as-errors"></a>將警告視為錯誤

**問**：我的專案使用 build 選項將警告視為錯誤。 從舊版分析遷移至原始程式碼分析之後，所有程式碼分析警告現在都會顯示為錯誤。 如何避免這種情況？

**答**：若要防止程式碼分析警告被視為錯誤，請遵循下列步驟：

  1. 使用下列內容建立 .props 檔案：

     ```xml
     <Project>
        <PropertyGroup>
           <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
        </PropertyGroup>
     </Project>
     ```

  2. 在您的 .csproj 或. vbproj 專案檔中新增一行，以匯入您在上一個步驟中建立的 .props 檔案。 這一行必須放在匯入 FxCop 分析器. .props 檔案的任何行之前。 例如，如果您的 .props 檔案名為 codeanalysis. .props：

     ```xml
     ...
     <Import Project="..\..\codeanalysis.props" Condition="Exists('..\..\codeanalysis.props')" />
     <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.5\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
     ...
     ```

## <a name="see-also"></a>另請參閱

- [分析器總覽](roslyn-analyzers-overview.md)
- [EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)
