---
title: 維護性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a2efe3e8d2d8c00a4fb016250f06943db46120c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649265"
---
# <a name="maintainability-warnings"></a>維護性警告

可維護性警告支援程式庫和應用程式維護。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
|-----------|-----------------------------------|
| [CA1500：變數名稱不應該與功能變數名稱相符 ](../code-quality/ca1500.md) | 實例方法會宣告參數或區域變數，其名稱符合宣告類型的實例欄位，因而導致錯誤。 |
| [CA1501：避免過度繼承 ](../code-quality/ca1501.md) | 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。 太深的巢狀類型階層架構可能會難以依循、了解和維護。 |
| [CA1502：避免過度複雜 ](../code-quality/ca1502.md) | 這個規則會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。 |
| [CA1504：查看誤導的功能變數名稱 ](../code-quality/ca1504.md) | 實例欄位的名稱是以 "s_" 開頭，或靜態的名稱（[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的共用）欄位是以 "m_" 開頭。 |
| [CA1505：避免撰寫無法維護程式碼 ](../code-quality/ca1505.md) | 類型或方法的維護性指標值很低。 維護性指標很低代表類型或方法很可能會難以維護，而應該列為需要重新設計的候選目標。 |
| [CA1506：避免過度的類別結合 ](../code-quality/ca1506.md) | 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。 |
| [CA1507：使用 nameof 取代字串 ](../code-quality/ca1507.md) | 字串常值是用來做為可使用 `nameof` 運算式的引數。 |

## <a name="see-also"></a>另請參閱

- [測量 Managed 程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)
