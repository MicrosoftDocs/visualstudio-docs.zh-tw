---
title: 'CA1815: Override equals and operator equals on value types | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 9b4cd8ddc4d5029a81e35460fa19373e69e33330
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Override equals and operator equals on value types
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Category|Microsoft.Performance|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A public value type does not override <xref:System.Object.Equals%2A?displayProperty=fullName>, or does not implement the equality operator (==). This rule does not check enumerations.  
  
## <a name="rule-description"></a>Rule Description  
 For value types, the inherited implementation of <xref:System.Object.Equals%2A> uses the Reflection library, and compares the contents of all fields. Reflection is computationally expensive, and comparing every field for equality might be unnecessary. If you expect users to compare or sort instances, or use them as hash table keys, your value type should implement <xref:System.Object.Equals%2A>. If your programming language supports operator overloading, you should also provide an implementation of the equality and inequality operators.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, provide an implementation of <xref:System.Object.Equals%2A>. If you can, implement the equality operator.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule if instances of the value type will not be compared to each other.  
  
## <a name="example-of-a-violation"></a>Example of a Violation  
  
### <a name="description"></a>Description  
 The following example shows a structure (value type) that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Example of How to Fix  
  
### <a name="description"></a>Description  
 The following example fixes the previous violation by overriding <xref:System.ValueType.Equals%2A?displayProperty=fullName> and implementing the equality operators (==, !=).  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2224: Override equals on overloading operator equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Overload operator equals on overriding ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Operators should have symmetrical overloads](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Object.Equals%2A?displayProperty=fullName>
