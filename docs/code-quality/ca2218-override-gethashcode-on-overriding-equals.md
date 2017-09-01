---
title: 'CA2218: Override GetHashCode on overriding Equals | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 9ad25f33c609d2bbb99aeb90f2fb844744a69013
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Override GetHashCode on overriding Equals
|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A public type overrides <xref:System.Object.Equals%2A?displayProperty=fullName> but does not override <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Rule Description  
 <xref:System.Object.GetHashCode%2A> returns a value, based on the current instance, that is suited for hashing algorithms and data structures such as a hash table. Two objects that are the same type and are equal must return the same hash code to ensure that instances of the following types work correctly:  
  
-   <xref:System.Collections.Hashtable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Types that implement <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, provide an implementation of <xref:System.Object.GetHashCode%2A>. For a pair of objects of the same type, you must ensure that the implementation returns the same value if your implementation of <xref:System.Object.Equals%2A> returns `true` for the pair.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="class-example"></a>Class Example  
  
### <a name="description"></a>Description  
 The following example shows a class (reference type) that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### <a name="comments"></a>Comments  
 The following example fixes the violation by overriding <xref:System.Object.GetHashCode>.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
## <a name="structure-example"></a>Structure Example  
  
### <a name="description"></a>Description  
 The following example shows a structure (value type) that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
### <a name="comments"></a>Comments  
 The following example fixes the violation by overriding <xref:System.Object.GetHashCode>.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1046: Do not overload operator equals on reference types](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operator overloads have named alternates](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operators should have symmetrical overloads](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Override equals on overloading operator equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Overload operator equals on overriding ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.Hashtable?displayProperty=fullName>   
 [Equality Operators](/dotnet/standard/design-guidelines/equality-operators)
