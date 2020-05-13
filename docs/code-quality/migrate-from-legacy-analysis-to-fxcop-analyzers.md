---
title: 從舊版分析（FxCop）遷移至來源分析（FxCop 分析器）
description: 瞭解如何第一次分析程式碼，或如何從二進位分析（FxCop）遷移至使用來源分析（FxCop 分析器）分析 managed 程式碼的新方式。
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937578"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>從舊版分析（FxCop）遷移至來源分析（FxCop 分析器）

.NET Compiler Platform （"Roslyn"）分析器的來源分析會取代 managed 程式碼的[舊版分析](../code-quality/code-analysis-for-managed-code-overview.md)。 若為較新的專案範本，例如 .NET Core 和 .NET Standard 專案，則無法使用舊版分析。

許多舊版分析（FxCop）規則已針對 FxCop 分析器（一組 Roslyn 程式碼分析器）重寫。 您會將[FxCop 分析器安裝為](install-fxcop-analyzers.md#nuget-package)專案或方案所參考的 NuGet 套件。 FxCop 分析器會在編譯器執行期間執行以原始程式碼為基礎的分析。 分析器結果會與編譯器結果一併回報。

如需舊版分析與來源分析之間差異的詳細資訊，請參閱下列各項：

- [原始碼分析與舊版分析](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [FxCop 分析器的常見問題](../code-quality/fxcop-analyzers-faq.md)

若要遷移至來源分析，請[安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)。 如同舊版分析規則違規，原始程式碼分析違規會出現在 Visual Studio 的 [錯誤清單] 視窗中。 此外，原始程式碼的分析違規也會在程式碼編輯器中顯示為*波浪線*在違規程序代碼之下。 波形曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#rule-severity)。 若要查看已移植到新 FxCop 分析器之規則的狀態，請參閱[移植和 unported license 規則](../code-quality/fxcop-rule-port-status.md)。

若要深入瞭解如何設定 FxCop 分析器：

- 若要設定 FxCop 分析器，請參閱[設定 fxcop 分析器](../code-quality/configure-fxcop-analyzers.md)。

- 若要瞭解如何使用預先定義的規則搭配 EditorConfig 或規則集檔案來設定分析器，請參閱[啟用分類的規則](../code-quality/analyzer-rule-sets.md)。