---
title: CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dbd8580f5aaeb88c08d35b50258510cb1a85ba2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920294"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
公用類型會覆<xref:System.Object.Equals%2A?displayProperty=fullName>寫, 但不<xref:System.Object.GetHashCode%2A?displayProperty=fullName>會覆寫。

## <a name="rule-description"></a>規則描述
 <xref:System.Object.GetHashCode%2A>根據目前的實例傳回值, 這適合用於雜湊演算法和資料結構 (例如雜湊資料表)。 相同類型且相等的兩個物件, 必須傳回相同的雜湊碼, 以確保下列類型的實例能夠正常運作:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- 執行的類型<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請提供的<xref:System.Object.GetHashCode%2A>執行。 對於相同類型的一對物件, 您必須確定如果的實<xref:System.Object.Equals%2A> `true`作為的傳回, 則此實作為會傳回相同的值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="class-example"></a>類別範例

### <a name="description"></a>描述
下列範例顯示違反此規則的類別 (參考型別)。

### <a name="code"></a>程式碼
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>註解
下列範例會藉由覆寫<xref:System.Object.GetHashCode>來修正違規。

### <a name="code"></a>程式碼
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>結構範例

### <a name="description"></a>說明
下列範例顯示違反此規則的結構 (實值型別)。

### <a name="code"></a>程式碼
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>註解
下列範例會藉由覆寫<xref:System.Object.GetHashCode>來修正違規。

### <a name="code"></a>程式碼
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>相關規則
[CA1046不要多載參考型別上的運算子 equals](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225運算子多載具有已命名的替代項](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224多載運算子 equals 的覆寫 equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)