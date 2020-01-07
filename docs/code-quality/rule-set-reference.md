---
title: 程式碼分析規則集參考
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d380346b7e049a6ffc4e8d03a5be27983de10249
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587234"
---
# <a name="code-analysis-rule-set-reference"></a>程式碼分析規則集參考

當您在 Visual Studio 中設定 managed 程式碼專案的舊版分析時，可以從內建*規則集*清單中選擇。 有些規則會包含在多個內建規則集中，例如，基本正確性規則規則集會包含受管理的建議規則規則集內的規則。

> [!NOTE]
> 本節中的規則集與舊版分析相關。 如需適用于程式碼分析器封裝之規則集的詳細資訊，請參閱搭配[使用規則集與程式碼](analyzer-rule-sets.md)分析器。

您可以使用其中一個內建規則集，也可以[自訂規則集](../code-quality/how-to-create-a-custom-rule-set.md)以符合您的專案需求。 如果您在自訂規則集中包含多個包含相同規則的規則集，該規則只會出現在自訂規則集中一次。

本節中的主題描述內建的規則集及其包含的規則（或警告）。

| 規則集 | 包含的規則 |
| - | - |
| [所有規則](all-rules-rule-set.md) | 包含所有可用的受控C++和規則 |
| [基本正確性規則](basic-correctness-rules-rule-set-for-managed-code.md) | 包括受管理的建議規則，以及邏輯錯誤和架構使用方式的規則 |
| [擴充的正確性規則](extended-correctness-rules-rule-set-for-managed-code.md) | 包含基本正確性規則（包括受管理的建議規則），再加上邏輯錯誤和架構使用方式的更多規則 |
| [基本設計指導方針規則](basic-design-guideline-rules-rule-set-for-managed-code.md) | 包括受管理的建議規則，以及確保程式碼容易閱讀、瞭解和維護的規則 |
| [擴充的設計方針規則](extended-design-guidelines-rules-rule-set-for-managed-code.md) | 包含基本的設計指導方針規則（包括受管理的建議規則），再加上著重于命名的更多維護性規則 |
| [全球化規則](globalization-rules-rule-set-for-managed-code.md) | 包含全球化問題的規則 |
| [受管理的最小規則](managed-minimum-rules-rule-set-for-managed-code.md) | 包含四個重大受控碼問題的規則 |
| [受管理的建議規則](managed-recommended-rules-rule-set-for-managed-code.md) | 包括受管理的最小規則，以及更多重要 managed 程式碼問題的規則 |
| [混合最小規則](mixed-minimum-rules-rule-set.md) | 包含 CLR 程式碼中C++重大問題的規則 |
| [混合的建議規則](mixed-recommended-rules-rule-set.md) | 包含混合的最小規則，再加上 CLR C++程式碼中嚴重問題的更多規則 |
| [原生最小規則](native-minimum-rules-rule-set.md) | 包含機器碼中重大問題的規則 |
| [原生建議規則](native-recommended-rules-rule-set.md) | 包括原生最小規則，以及機器碼中嚴重問題的更多規則 |
| [安全性規則](security-rules-rule-set-for-managed-code.md) | 包含尋找安全性弱點的規則 |
