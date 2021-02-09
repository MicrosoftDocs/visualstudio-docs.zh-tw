---
title: 程式碼分析規則集參考
ms.date: 04/04/2018
description: 瞭解 Visual Studio 舊版程式碼分析中的內建規則集。 請參閱規則集上的資源。 瞭解如何在自訂規則集中使用這些集合。
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cead2d51a13ce4ec137edcd55c7db91d84b04f7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867772"
---
# <a name="code-analysis-rule-set-reference"></a>程式碼分析規則集參考

當您針對 Visual Studio 中的 managed 程式碼專案設定舊版分析時，可以從內建 *規則集* 的清單中選擇。 某些規則包含在一個以上的內建規則集中，例如，基本正確性規則規則集包含受管理的建議規則規則集中的規則。

> [!NOTE]
> 本節中的規則集與舊版分析相關。 如需適用于程式碼分析器套件之規則集的詳細資訊，請參閱 [使用規則集](/dotnet/fundamentals/code-analysis/code-quality-rule-options)搭配程式碼分析器。

您可以使用其中一個內建規則集，也可以 [自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md) 以符合您的專案需求。 如果您將多個規則集包含在自訂規則集中的相同規則，該規則只會在自訂規則集中出現一次。

本節中的主題描述內建的規則集，以及它們所包含)  (或警告的規則。

| 規則集 | 包含的規則 |
| - | - |
| [所有規則](all-rules-rule-set.md) | 包含所有可用的 managed 和 c + + 規則 |
| [基本正確性規則](basic-correctness-rules-rule-set-for-managed-code.md) | 包含受管理的建議規則，以及邏輯錯誤和架構使用方式的規則 |
| [延伸正確性規則](extended-correctness-rules-rule-set-for-managed-code.md) | 包含基本的正確性規則 (包括受控建議規則) 再加上邏輯錯誤和架構使用方式的更多規則 |
| [基本設計指導方針規則](basic-design-guideline-rules-rule-set-for-managed-code.md) | 包含受管理的建議規則，以及可確保程式碼易於閱讀、瞭解和維護的規則 |
| [延伸設計指導方針規則](extended-design-guidelines-rules-rule-set-for-managed-code.md) | 包含基本的設計指導方針規則 (包括受控建議規則) 再加上更多可維護性的規則，以供命名 |
| [全球化規則](globalization-rules-rule-set-for-managed-code.md) | 包含全球化問題的規則 |
| [受控最小規則](managed-minimum-rules-rule-set-for-managed-code.md) | 包含四項重大 managed 程式碼問題的規則 |
| [受控建議規則](managed-recommended-rules-rule-set-for-managed-code.md) | 包含受管理的最小規則，以及重要 managed 程式碼問題的更多規則 |
| [混合最小規則](mixed-minimum-rules-rule-set.md) | 包含 CLR c + + 程式碼中重大問題的規則 |
| [混合建議規則](mixed-recommended-rules-rule-set.md) | 針對 CLR 的 c + + 程式碼中的重大問題，包括混合的最小規則和更多規則 |
| [原生最小規則](native-minimum-rules-rule-set.md) | 包含機器碼中重大問題的規則 |
| [原生建議規則](native-recommended-rules-rule-set.md) | 包含原生程式碼中重大問題的原生最小規則和更多規則 |
| [安全性規則](security-rules-rule-set-for-managed-code.md) | 包含找出安全性弱點的規則 |