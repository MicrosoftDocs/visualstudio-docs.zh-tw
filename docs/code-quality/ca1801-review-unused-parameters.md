---
title: 'CA1801: Review unused parameters | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 30
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
ms.openlocfilehash: 3c640bad82bd7e84cafe1dcab69f565a9e6222c4
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Review unused parameters
|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|CheckId|CA1801|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking - If the member is not visible outside the assembly, regardless of the change you make.<br /><br /> Non Breaking - If you change the member to use the parameter within its body.<br /><br /> Breaking - If you remove the parameter and it is visible outside the assembly.|  
  
## <a name="cause"></a>Cause  
 A method signature includes a parameter that is not used in the method body. This rule does not examine the following methods:  
  
-   Methods referenced by a delegate.  
  
-   Methods used as event handlers.  
  
-   Methods declared with the `abstract` (`MustOverride` in Visual Basic) modifier.  
  
-   Methods declared with the `virtual` (`Overridable` in Visual Basic) modifier.  
  
-   Methods declared with the `override` (`Overrides` in Visual Basic) modifier.  
  
-   Methods declared with the `extern` (`Declare` statement in Visual Basic) modifier.  
  
## <a name="rule-description"></a>Rule Description  
 Review parameters in non-virtual methods that are not used in the method body to make sure no correctness exists around failure to access them. Unused parameters incur maintenance and performance costs.  
  
 Sometimes a violation of this rule can point to an implementation bug in the method. For example, the parameter should have been used in the method body. Suppress warnings of this rule if the parameter has to exist because of backward compatibility.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, remove the unused parameter (a breaking change) or use the parameter in the method body (a non-breaking change).  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule for previously shipped code for which the fix would be a breaking change.  
  
## <a name="example"></a>Example  
 The following example shows two methods. One method violates the rule and the other method satisfies the rule.  
  
 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1811: Avoid uncalled private code](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Avoid uninstantiated internal classes](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Remove unused locals](../code-quality/ca1804-remove-unused-locals.md)
