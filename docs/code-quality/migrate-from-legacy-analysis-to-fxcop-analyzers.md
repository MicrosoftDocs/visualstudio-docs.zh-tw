---
title: '從 FxCop 遷移至來源分析 (FxCop 分析器) '
ms.custom: SEO-VS-2020
description: 瞭解如何首次分析程式碼，或如何從二進位分析 (FxCop) 遷移至使用來源分析 (FxCop 分析器) 來分析 managed 程式碼的新方法。
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
ms.openlocfilehash: 2109d7cbcaaf56600812e27c3055fb3198848228
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810203"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>從舊版分析 (FxCop) 遷移至來源分析 (FxCop 分析器) 

.NET Compiler Platform ( "Roslyn" 的來源分析 ) 分析器會取代 managed 程式碼的 [舊版分析](../code-quality/code-analysis-for-managed-code-overview.md) 。 針對較新的專案範本（例如 .NET Core 和 .NET Standard 專案），無法使用舊版分析。

許多舊版分析 (FxCop) 規則已針對 FxCop 分析器重寫，這是一組 Roslyn 程式碼分析器。 您將 [FxCop 分析器安裝為](install-fxcop-analyzers.md#nuget-package) 專案或解決方案所參考的 NuGet 套件。 FxCop 分析器會在編譯器執行期間執行以原始程式碼為基礎的分析。 分析器結果會與編譯器結果一併回報。

如需舊版分析和來源分析之間差異的詳細資訊，請參閱下列各項：

- [原始碼分析與舊版分析](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [FxCop 分析器的常見問題](../code-quality/fxcop-analyzers-faq.md)

若要遷移至來源分析，請 [安裝 FxCop 分析器](../code-quality/install-fxcop-analyzers.md)。 如同舊版分析規則違規，原始程式碼分析違規會出現在 Visual Studio 的 [錯誤清單] 視窗中。 此外，來來源程式代碼分析違規也會在程式碼編輯器中顯示為有問題的程式碼下的 *波浪線* 。 波形曲線色彩取決於規則的[嚴重性設定](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)。 若要查看已移植至新 FxCop 分析器之規則的狀態，請參閱 [移植和 unported 規則](../code-quality/fxcop-rule-port-status.md)。

若要深入瞭解如何設定 FxCop 分析器：

- 若要設定 FxCop 分析器，請參閱 [設定 fxcop 分析器](../code-quality/configure-fxcop-analyzers.md)。

- 若要瞭解如何使用預先定義的規則搭配 EditorConfig 或規則集檔案來設定分析器，請參閱 [啟用規則的類別](../code-quality/analyzer-rule-sets.md)。