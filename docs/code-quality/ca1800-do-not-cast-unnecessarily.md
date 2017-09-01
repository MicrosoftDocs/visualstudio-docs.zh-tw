---
title: 'CA1800: Do not cast unnecessarily | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
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
ms.openlocfilehash: e2c0d1e5c21661d1a6cc61f7ba7307812bb6a98b
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Do not cast unnecessarily
|||  
|-|-|  
|TypeName|DoNotCastUnnecessarily|  
|CheckId|CA1800|  
|Category|Microsoft.Performance|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A method performs duplicate casts on one of its arguments or local variables. For complete analysis by this rule, the tested assembly must be built by using debugging information and the associated program database (.pdb) file must be available.  
  
## <a name="rule-description"></a>Rule Description  
 Duplicate casts decrease performance, especially when the casts are performed in compact iteration statements. For explicit duplicate cast operations, store the result of the cast in a local variable and use the local variable instead of the duplicate cast operations.  
  
 If the C# `is` operator is used to test whether the cast will succeed before the actual cast is performed, consider testing the result of the `as` operator instead. This provides the same functionality without the implicit cast operation that is performed by the `is` operator.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, modify the method implementation to minimize the number of cast operations.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule, or to ignore the rule completely, if performance is not a concern.  
  
## <a name="example"></a>Example  
 The following example shows a method that violates the rule by using the C# `is` operator. A second method satisfies the rule by replacing the `is` operator with a test against the result of the `as` operator, which decreases the number of cast operations per iteration from two to one.  
  
 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]  
  
## <a name="example"></a>Example  
 The following example shows a method, `start_Click`, that has multiple duplicate explicit casts, which violates the rule, and a method, `reset_Click`, which satisfies the rule by storing the cast in a local variable.  
  
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)] [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]  
  
## <a name="see-also"></a>See Also  
 [as](/dotnet/csharp/language-reference/keywords/as)   
 [is](/dotnet/csharp/language-reference/keywords/is)
