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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd7fe79665ac8de665116a6832d5ef9327fb356c
ms.sourcegitcommit: dab57cebd484228e6f0cf7ab1b9685c575410c06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82152983"
---
# <a name="maintainability-warnings"></a>維護性警告

可維護性警告支援程式庫和應用程式維護。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
|-----------|-----------------------------------|
| [CA1500：變數名稱不應該與欄位名稱相符](../code-quality/ca1500.md) | 實例方法會宣告參數或區域變數，其名稱符合宣告類型的實例欄位，因而導致錯誤。 |
| [CA1501：避免在物件間過度繼承](../code-quality/ca1501.md) | 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。 太深的巢狀類型階層架構可能會難以依循、了解和維護。 |
| [CA1502：避免造成過度複雜的方法](../code-quality/ca1502.md) | 這個規則會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。 |
| [CA1504：必須檢閱可能造成誤導的欄位名稱](../code-quality/ca1504.md) | 實例欄位的名稱開頭為 "s_"，或靜態（在中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]為共用）欄位的開頭為 "m_"。 |
| [CA1505：應避免撰寫無法維護的程式碼](../code-quality/ca1505.md) | 類型或方法的維護性指標值很低。 維護性指標很低代表類型或方法很可能會難以維護，而應該列為需要重新設計的候選目標。 |
| [CA1506：應避免使用結合過度的類別](../code-quality/ca1506.md) | 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。 |
| [CA1507：使用 nameof 取代字串](../code-quality/ca1507.md) | 字串常值是用來做為可使用`nameof`運算式的引數。 |
| [CA1508：避免失效的條件式程式碼](../code-quality/ca1508.md) | 方法具有條件式程式碼，一律會`true`在`false`執行時間評估為或。 這會導致條件`false`分支中的無作用程式碼。 |

## <a name="see-also"></a>另請參閱

- [測量 Managed 程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)
