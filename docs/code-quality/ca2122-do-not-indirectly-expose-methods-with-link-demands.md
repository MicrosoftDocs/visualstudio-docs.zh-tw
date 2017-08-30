---
title: 'CA2122: Do not indirectly expose methods with link demands | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
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
ms.openlocfilehash: 9996d217691c9a21701c1f6f36e7ced8f605efe0
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Do not indirectly expose methods with link demands
|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Category|Microsoft.Security|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected member has a [Link Demands](/dotnet/framework/misc/link-demands) and is called by a member that does not perform any security checks.  
  
## <a name="rule-description"></a>Rule Description  
 A link demand checks the permissions of the immediate caller only. If a member `X` makes no security demands of its callers, and calls code protected by a link demand, a caller without the necessary permission can use `X` to access the protected member.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 Add a security [Data and Modeling](/dotnet/framework/data/index) or link demand to the member so that it no longer provides unsecured access to the link demand-protected member.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 To safely suppress a warning from this rule, you must make sure that your code does not grant its callers access to operations or resources that can be used in a destructive manner.  
  
## <a name="example"></a>Example  
 The following examples show a library that violates the rule, and an application that demonstrates the library's weakness. The sample library provides two methods that together violate the rule. The `EnvironmentSetting` method is secured by a link demand for unrestricted access to environment variables. The `DomainInformation` method makes no security demands of its callers before it calls `EnvironmentSetting`.  
  
 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## <a name="example"></a>Example  
 The following application calls the unsecured library member.  
  
 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 This example produces the following output.  
  
 **Value from unsecured member: seattle.corp.contoso.com**   
## <a name="see-also"></a>See Also  
 [Secure Coding Guidelines](/dotnet/standard/security/secure-coding-guidelines)   
 [Link Demands](/dotnet/framework/misc/link-demands)   
 [Data and Modeling](/dotnet/framework/data/index)
