---
title: CA2224：多載運算子 equals 的覆寫 equals |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538632"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224:多載等號比較運算子時必須一併覆寫 Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型會執行等號比較運算子，但不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 等號比較運算子的目的是以語法方便的方式來存取方法的功能 <xref:System.Object.Equals%2A> 。 如果您執行等號比較運算子，其邏輯必須與相同 <xref:System.Object.Equals%2A> 。

 如果您的程式碼違反此規則，c # 編譯器會發出警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，您應該移除等號比較運算子的執行，或覆寫 <xref:System.Object.Equals%2A> 並讓兩個方法傳回相同的值。 如果等號比較運算子不會造成不一致的行為，您可以藉由提供 <xref:System.Object.Equals%2A> 會呼叫基類中方法的執行來修正違規 <xref:System.Object.Equals%2A> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果等號比較運算子傳回的值與繼承的執行相同，就可以安全地隱藏此規則的警告 <xref:System.Object.Equals%2A> 。 範例區段包含的類型，可以安全地隱藏此規則的警告。

## <a name="examples-of-inconsistent-equality-definitions"></a>不一致的相等定義範例

### <a name="description"></a>描述
 下列範例顯示具有不一致之相等定義的類型。 `BadPoint`藉由提供等號比較運算子的自訂執行來變更相等的意義，但不會覆寫， <xref:System.Object.Equals%2A> 因此其行為完全相同。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>範例
 下列程式碼會測試的行為 `BadPoint` 。

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 此範例會產生下列輸出。

 **a = （[0] 1，1）和 b = （[1] 2，2）相等嗎？否** 
 **a = = b？沒有** 
 **a1 和 a 相等嗎？是** 
 **a1 = = a？是** 
 **b，bcopy 相等嗎？否** 
 **b = = bcopy？是**
## <a name="example"></a>範例
 下列範例顯示技術上違反此規則的類型，但不會有不一致的行為。

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>範例
 下列程式碼會測試的行為 `GoodPoint` 。

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 此範例會產生下列輸出。

 **a = （1，1）和 b = （2，2）相等嗎？否** 
 **a = = b？沒有** 
 **a1 和 a 相等嗎？是** 
 **a1 = = a？是** 
 **b，bcopy 相等嗎？是** 
 **b = = bcopy？是**
## <a name="class-example"></a>類別範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的類別（參考型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>範例
 下列範例會藉由覆寫來修正違規 <xref:System.Object.Equals%2A?displayProperty=fullName> 。

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>結構範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的結構（實值型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>範例
 下列範例會藉由覆寫來修正違規 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 。

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225:運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226:運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
