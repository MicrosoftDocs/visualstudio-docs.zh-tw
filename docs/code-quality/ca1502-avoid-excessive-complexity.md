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
ms.workload:
- multiple
ms.openlocfilehash: a532207bf8e002dbde92bb85115c35b4de954c48
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919035"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502：避免過度複雜
|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|分類|Microsoft.Maintainability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法有過多的循環複雜度。

## <a name="rule-description"></a>規則描述
 *循環複雜度*會測量整個方法，取決於的數目與複雜度的條件式分支中線性獨立路徑的數目。 較低的循環複雜度，通常表示可以輕鬆地了解、 測試和維護的方法。 循環複雜度計算從控制流程圖表的方法，並提供，如下所示：

 循環複雜度 = 邊緣-的節點數目 + 1 的數目

 其中一個節點代表一個邏輯分支點和邊緣表示節點之間的線。

 循環複雜度是多個 25 時，此規則會報告發生違規。

 您可以進一步了解在程式碼度量[測量複雜度和維護性 Managed 程式碼的](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)，

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，重構的方法，以降低循環複雜度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果無法輕易降低複雜性，而方法為容易了解、 測試和維護。 特別是方法，可包含大型`switch`(`Select`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 陳述式會排除的候選項目。 造成不穩定的程式碼基底中開發週期或引入預期的變更在先前提供之程式碼的執行階段行為中的晚期帶來可維護性的優點重構程式碼的風險。

## <a name="how-cyclomatic-complexity-is-calculated"></a>循環複雜度的計算方式
 循環複雜度計算方式是將 1 所示：

-   分支的數目 (例如`if`， `while`，和`do`)

-   數目`case`中的陳述式 `switch`

 下列範例顯示具有不同的循環複雜度的方法。

## <a name="example"></a>範例
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
 **3 的循環複雜度**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>範例
 **循環複雜度為 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1501：避免在物件間過度繼承](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜度和維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)