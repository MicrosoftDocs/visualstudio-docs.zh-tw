---
title: 'CA2143: Transparent methods should not use security demands | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 12
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
ms.openlocfilehash: 7a1a4fc4f5b76137c59b73a8fd42e12fac1b1d3e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparent methods should not use security demands
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A tranparent type or method is declaratively marked with a <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>`.Demand` demand or the method calls the <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> method.  
  
## <a name="rule-description"></a>Rule Description  
 Security transparent code should not be responsible for verifying the security of an operation, and therefore should not demand permissions. Security transparent code should use full demands to make security decisions and safe-critical code should not rely on transparent code to have made the full demand. Any code that performs security checks, such as security demands, should be safe-critical instead.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 In general, to fix a violation of this rule, mark the method with the <xref:System.Security.SecuritySafeCriticalAttribute> attribute. You can also remove the demand.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The rule files on the following code because a transparent method makes a declarative security demand.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>See Also  
 [CA2142: Transparent code should not be protected with LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
