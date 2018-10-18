---
title: CA2224： 多載等號比較運算子的覆寫 equals |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 64b5c7113b5616733b6528cf0790f25211e18f6c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192865"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224：多載等號比較運算子時必須一併覆寫 Equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用類型會實作等號比較運算子，但不會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 等號比較運算子就是要在語法上方便存取的功能<xref:System.Object.Equals%2A>方法。 如果您實作等號比較運算子，其邏輯必須是相同<xref:System.Object.Equals%2A>。

 如果您的程式碼違反此規則，C# 編譯器會發出警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，您應該移除的等號比較運算子的實作，或覆寫<xref:System.Object.Equals%2A>和有兩種方法會傳回相同的值。 如果等號比較運算子不會提供不一致的行為，您可以藉由提供的實作來修正違規<xref:System.Object.Equals%2A>呼叫<xref:System.Object.Equals%2A>基底類別中的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 安全地隱藏此規則的警告，等號比較運算子傳回的繼承實作相同的值如果<xref:System.Object.Equals%2A>。 範例 > 一節包含類型，可放心地隱藏此規則的警告。

## <a name="examples-of-inconsistent-equality-definitions"></a>不一致的等號比較定義的範例

### <a name="description"></a>描述
 下列範例示範具有相等的定義不一致的型別。 `BadPoint` 藉由提供自訂實作等號比較運算子中，變更是否相等的意義，但不會覆寫<xref:System.Object.Equals%2A>，讓它的行為相同。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>範例
 下列程式碼測試的行為`BadPoint`。

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 此範例會產生下列輸出。

 **a = ([0] 1，1) 和 b = ([1] 2，2) 相等嗎？否**
 **= = b？否**
**a1 和 a 等於嗎？[是]**
**a1 = = 嗎？[是]**
**b 和 bcopy 相等嗎？否**
**b = = bcopy 嗎？[是]**
## <a name="example"></a>範例
 下列範例會示範一種類型，就技術上而言違反這項規則，但不是會不一致的方式運作。

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>範例
 下列程式碼測試的行為`GoodPoint`。

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 此範例會產生下列輸出。

 **a = (1，1) 和 b = (2，2) 相等嗎？否**
 **= = b？否**
**a1 和 a 等於嗎？[是]**
**a1 = = 嗎？[是]**
**b 和 bcopy 相等嗎？[是]**
**b = = bcopy 嗎？[是]**
## <a name="class-example"></a>類別的範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的類別 （參考型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>範例
 下列範例會藉由覆寫修正違規<xref:System.Object.Equals%2A?displayProperty=fullName>。

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>結構範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的結構 （數值型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>範例
 下列範例會藉由覆寫修正違規<xref:System.ValueType.Equals%2A?displayProperty=fullName>。

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225：運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



