---
title: CA1502：避免過度複雜
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8eaaaa8b810e79b2bd1a4da0ab1d9887c8a46380
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440122"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502：避免過度複雜

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|分類|Microsoft。可維護性|
|重大變更|不中斷|

## <a name="cause"></a>原因

方法的迴圈複雜度過大。

## <a name="rule-description"></a>規則描述

*圈複雜度*會測量透過方法的線性獨立路徑數目，這取決於條件式分支的數目和複雜度。 較低的圈複雜度通常表示容易瞭解、測試和維護的方法。 迴圈複雜度是從方法的控制流程圖來計算，並以下列方式提供：

圈複雜度 = 邊緣數目-節點數目 + 1

*節點*代表邏輯分支點，而*邊緣*代表節點之間的線條。

當圈複雜度大於25時，此規則會報告違規。

您可以在[managed 程式碼的測量複雜度](../code-quality/code-metrics-values.md)中深入瞭解程式碼度量。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請重構方法，以降低其圈複雜度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果無法輕易降低複雜性，而且方法很容易瞭解、測試和維護，就可以放心地隱藏此規則的警告。 特別的是，包含大型 `switch` 的方法（在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中 `Select`）語句是排除的候選項。 在開發週期中不穩定程式碼基底的風險，或在先前隨附的程式碼中引進執行時間行為的非預期變更，可能會超過重構程式碼的維護性優勢。

## <a name="how-cyclomatic-complexity-is-calculated"></a>如何計算圈複雜度

迴圈複雜度的計算方式是將1新增至下列內容：

- 分支的數目（例如 `if`、`while` 和 `do`）

- @No__t 中的 `case` 語句數-1

## <a name="example"></a>範例

下列範例顯示迴圈複雜度不同的方法。

**1的圈複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>範例

**2的圈複雜度**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>範例

**圈複雜度為3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>範例

**量的圈複雜度為8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>相關規則

[CA1501：避免在物件間過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>請參閱

- [測量 Managed 程式碼的複雜度和維護性](../code-quality/code-metrics-values.md)
