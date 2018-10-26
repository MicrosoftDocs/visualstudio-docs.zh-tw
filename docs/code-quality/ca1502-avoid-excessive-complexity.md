---
title: CA1502：避免過度複雜
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfa12a2a1ade8d32c5518660c46ce79bc997d776
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819299"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502：避免過度複雜

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|分類|Microsoft.Maintainability|
|中斷變更|非重大|

## <a name="cause"></a>原因

方法具有過多的循環複雜度。

## <a name="rule-description"></a>規則描述

*循環複雜度*測量透過方法，取決於的數目和複雜度的條件式分支中線性獨立路徑數目。 較低的循環複雜度通常表示可以輕鬆地了解、 測試和維護的方法。 循環複雜度會計算從控制流程圖形的方法，並指定，如下所示：

循環複雜度 = 邊緣-的節點數目 + 1 的數目

其中一個節點代表一個邏輯分支點和邊緣，表示節點之間的線條。

循環複雜度超過 25 項時，此規則會報告違規情形。

您可以深入了解在程式碼度量[測量的複雜性和可維護性的 Managed 程式碼](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)，

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，重構的方法，以降低循環複雜度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告，如果無法輕易地降低複雜度和方法很容易了解、 測試和維護。 特別是方法，可包含大型`switch`(`Select`在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 陳述式是排除的候選項目。 Code 的風險會延遲在開發週期，或導致執行階段行為，先前隨附的程式碼中發生意外的變更可能會大於效益可維護性的重構程式碼基底的程式碼。

## <a name="how-cyclomatic-complexity-is-calculated"></a>循環複雜度的計算方式

循環複雜度計算方式是將 1 所示：

- 分支數 (例如`if`， `while`，和`do`)

- 數目`case`中的陳述式 `switch`

## <a name="example"></a>範例

下列範例顯示具有不同的循環複雜度的方法。

**1 的循環複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>範例

**2 的循環複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>範例

**為 3 的循環複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>範例

**8 個循環複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>相關的規則

[CA1501：避免在物件間過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>另請參閱

- [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)