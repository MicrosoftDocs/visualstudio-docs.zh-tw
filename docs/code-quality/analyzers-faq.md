---
title: EditorConfig 與分析器
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzers, faq
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bec9296f15c48cf3b327c78cd0ce7d57adafa002
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62571468"
---
# <a name="analyzers-faq"></a>分析器常見問題集

此頁面包含一些常見的問題，需在 Visual Studio 中的 Roslyn 分析器的解答。

## <a name="roslyn-analyzers-versus-editorconfig"></a>與.editorconfig 的 Roslyn 分析器

**問：**:我應該使用 Roslyn 分析器或.editorconfig 的程式碼樣式？

**答**：Roslyn 分析器和.editorconfig 檔案運作中手狀游標。 當您定義程式碼樣式[.editorconfig 檔案中](../ide/editorconfig-code-style-settings-reference.md)或在[文字編輯器選項](../ide/code-styles-and-quick-actions.md) 頁面上，您實際上設定 Visual Studio 內建的 Roslyn 分析器。 EditorConfig 檔案也可用來設定一些第三方分析器套件，例如[FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="editorconfig-versus-rule-sets"></a>EditorConfig 與規則集

**問：**:應設定使用的規則集或.editorconfig 檔案，我分析器？

**答**：規則集和.editorconfig 檔案是互斥的方式設定分析器。 它們可以同時存在。 [規則集](analyzer-rule-sets.md)可讓您啟用和停用規則並設定其嚴重性。 EditorConfig 檔案可提供其他方式來設定規則。 FxCop 分析器.editorconfig 檔案可讓您[定義何種類型的程式碼，以分析](fxcop-analyzer-options.md)。 針對 Visual Studio 內建分析器，.editorconfig 檔案可讓您[定義慣用的程式碼樣式](../ide/editorconfig-code-style-settings-reference.md)程式碼基底。

某些協力廠商分析器設定透過標示的文字檔案使用規則集和.editorconfig 檔案，除了[額外的檔案](../ide/build-actions.md#build-action-values)的C#和 VB 編譯器。

> [!NOTE]
> EditorConfig 檔案不能用來設定靜態程式碼分析規則，而規則集可以。

## <a name="analyzers-in-ci-builds"></a>在 CI 組建的分析器

**問：**:在持續整合 (CI) 組建中，分析器工作嗎？

**答**：可以。 針對從 NuGet 套件安裝的分析器，這些規則都[強制執行在建置階段](roslyn-analyzers-overview.md#build-errors)，包括在 CI 組建期間。 從 CI 組建方面規則組態中所使用的分析器[規則集](analyzer-rule-sets.md)並[.editorconfig 檔案](configure-fxcop-analyzers.md)。 目前，Visual Studio 內建的程式碼分析器不是以 NuGet 套件，可用，所以這些規則是不強制在 CI 組建。

## <a name="ide-analyzers-versus-stylecop"></a>與 StyleCop IDE 分析器

**問：**:在 Visual Studio IDE 的程式碼分析器和 StyleCop 分析器之間的差異為何？

**答**：Visual Studio IDE 包括內建的分析器，可尋找這兩個程式碼樣式和品質問題。 這些規則可協助您使用新語言功能，因為它們導入，並改善您的程式碼維護性。 IDE 分析器會持續更新每個 Visual Studio 版本。

[StyleCop 分析器](https://github.com/DotNetAnalyzers/StyleCopAnalyzers)都是第三方分析器，安裝為 NuGet 套件的程式碼中的樣式一致性檢查。 一般情況下，StyleCop 規則可讓您設定的程式碼的個人喜好設定的基底，而不透過另一個建議一種樣式。

## <a name="analyzers-versus-static-code-analysis"></a>分析器與靜態程式碼分析

**問：**:分析器和靜態程式碼分析之間的差異為何？

**答**：分析器來分析原始碼即時及在編譯期間，而組建完成後，靜態程式碼分析會分析二進位檔。 如需詳細資訊，請參閱 <<c0> [ 與靜態程式碼分析的 Roslyn 分析器](roslyn-analyzers-overview.md#roslyn-analyzers-vs-static-code-analysis)並[FxCop 分析器常見問題集](fxcop-analyzers-faq.md)。

## <a name="see-also"></a>另請參閱

- [分析器概觀](roslyn-analyzers-overview.md)
- [EditorConfig 的 .NET 編碼慣例設定](../ide/editorconfig-code-style-settings-reference.md)