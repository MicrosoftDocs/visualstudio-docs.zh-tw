---
title: 'CA2230: Use params for variable arguments | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 15
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
ms.openlocfilehash: 8e7037e7b642aa36bb1a351113e7d09dc1ea2537
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Use params for variable arguments
|||  
|-|-|  
|TypeName|UseParamsForVariableArguments|  
|CheckId|CA2230|  
|Category|Microsoft.Usage|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected type contains a public or protected method that uses the `VarArgs` calling convention.  
  
## <a name="rule-description"></a>Rule Description  
 The `VarArgs` calling convention is used with certain method definitions that take a variable number of parameters. A method using the `VarArgs` calling convention is not Common Language Specification (CLS) compliant and might not be accessible across programming languages.  
  
 In C#, the `VarArgs` calling convention is used when a method's parameter list ends with the `__arglist` keyword. Visual Basic does not support the `VarArgs` calling convention, and Visual C++  allows its use only in unmanaged code that uses the ellipse `...` notation.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule in C#, use the [params](/dotnet/csharp/language-reference/keywords/params) keyword instead of `__arglist`.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows two methods, one that violates the rule and one that satisfies the rule.  
  
 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]  
  
## <a name="see-also"></a>See Also  
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>   
 [Language Independence and Language-Independent Components](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
