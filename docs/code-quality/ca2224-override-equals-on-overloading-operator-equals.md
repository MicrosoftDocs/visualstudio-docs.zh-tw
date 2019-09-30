---
title: CA2224:多載等號比較運算子時必須一併覆寫 Equals
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231209"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224:多載等號比較運算子時必須一併覆寫 Equals

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

公用類型會執行等號比較運算子，但不會<xref:System.Object.Equals%2A?displayProperty=fullName>覆寫。

## <a name="rule-description"></a>規則描述

等號比較運算子的目的是以語法方便的方式來存取<xref:System.Object.Equals%2A>方法的功能。 如果您執行等號比較運算子，其邏輯必須與相同<xref:System.Object.Equals%2A>。

如果C#您的程式碼違反此規則，編譯器會發出警告。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，您應該移除等號比較運算子的執行，或覆寫<xref:System.Object.Equals%2A>並讓兩個方法傳回相同的值。 如果等號比較運算子不會造成不一致的行為，您可以藉由提供<xref:System.Object.Equals%2A>會<xref:System.Object.Equals%2A>呼叫基類中方法的執行來修正違規。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果等號比較運算子傳回的值與繼承的<xref:System.Object.Equals%2A>執行相同，就可以安全地隱藏此規則的警告。 本文中的範例包含可以安全地隱藏此規則之警告的類型。

## <a name="examples-of-inconsistent-equality-definitions"></a>不一致的相等定義範例

下列範例顯示具有不一致之相等定義的類型。 `BadPoint`藉由提供等號比較運算子的自訂執行來變更相等的意義，但不<xref:System.Object.Equals%2A>會覆寫，因此其行為完全相同。

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

下列程式碼會測試的行為`BadPoint`。

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

這個範例會產生下列輸出：

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

下列範例顯示技術上違反此規則的類型，但不會有不一致的行為。

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

下列程式碼會測試的行為`GoodPoint`。

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

這個範例會產生下列輸出：

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>類別範例

下列範例顯示違反此規則的類別（參考型別）。

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

下列範例會藉由覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>來修正違規。

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>結構範例

下列範例顯示違反此規則的結構（實數值型別）：

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

下列範例會藉由覆寫<xref:System.ValueType.Equals%2A?displayProperty=fullName>來修正違規。

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>相關規則

[CA1046不要多載參考型別上的運算子 equals](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225運算子多載具有已命名的替代項](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218覆寫覆寫 Equals 上的 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)