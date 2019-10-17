---
title: CA1013：多載加號和減號運算子時必須一併多載等號比較運算子
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 575afd3609da0e8f362408f8a1550303ec03cf3f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446725"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013：多載加號和減號運算子時必須一併多載等號比較運算子

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|分類|Microsoft. Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。

## <a name="rule-description"></a>規則描述
當類型的實例可以使用加法和減法之類的作業結合時，您幾乎都應該針對具有相同組成值的任何兩個實例，定義傳回 `true` 的相等。

在等號比較運算子的多載執行中，不能使用預設的等號比較運算子。 這麼做會造成堆疊溢位。 若要執行等號比較運算子，請在您的執行中使用 Equals 方法。 請參閱下列範例。

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請執行等號比較運算子，使其在數學上與加法和減法運算子一致。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
當等號比較運算子的預設執行提供類型的正確行為時，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例會定義違反此規則的類型（`BadAddableType`）。 這個型別應該會執行等號比較運算子，讓具有相同域值的兩個實例都 `true` 進行相等的測試。 類型 `GoodAddableType` 會顯示已更正的執行。 請注意，此類型也會執行不等比較運算子，並覆寫 <xref:System.Object.Equals%2A> 以滿足其他規則。 完整的執行也會執行 <xref:System.Object.GetHashCode%2A>。

[!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>範例
下列範例會使用先前在本主題中定義的類型實例來測試是否相等，以說明等號比較運算子的預設和正確行為。

[!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

這個範例會產生下列輸出：

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>請參閱

- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)
