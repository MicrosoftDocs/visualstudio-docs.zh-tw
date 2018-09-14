---
title: CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dda8fd453ae36e11a4d8f20780caf60bf3c915f0
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547785"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>，但不會覆寫<xref:System.Object.GetHashCode%2A?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 <xref:System.Object.GetHashCode%2A> 傳回值，根據目前的執行個體、 適用於雜湊演算法和資料結構，例如雜湊表。 相同的型別而且相等的兩個物件必須傳回相同的雜湊程式碼，以確保下列類型的執行個體，可正確運作：

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- 實作的型別 <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，提供實作<xref:System.Object.GetHashCode%2A>。 一組相同類型的物件中，您必須確定實作會傳回相同的值，如果您實作<xref:System.Object.Equals%2A>傳回`true`配對。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="class-example"></a>類別的範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的類別 （參考型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>註解
 下列範例會藉由覆寫修正違規<xref:System.Object.GetHashCode>。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>結構範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的結構 （數值型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>註解
 下列範例會藉由覆寫修正違規<xref:System.Object.GetHashCode>。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225：運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)