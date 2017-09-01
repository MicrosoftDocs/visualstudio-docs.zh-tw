---
title: 'CA2135: Level 2 assemblies should not contain LinkDemands | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 10
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
ms.openlocfilehash: b16b92994dd2ab0e03ade703460e52a887e820e6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Level 2 assemblies should not contain LinkDemands
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A class or class member is using a <xref:System.Security.Permissions.SecurityAction> in an application that is using Level 2 security.  
  
## <a name="rule-description"></a>Rule Description  
 LinkDemands are deprecated in the level 2 security rule set. Instead of using LinkDemands to enforce security at just-in-time (JIT) compilation time, mark the methods, types, and fields with the <xref:System.Security.SecurityCriticalAttribute> attribute.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, remove the <xref:System.Security.Permissions.SecurityAction> and mark the type or member with the <xref:System.Security.SecurityCriticalAttribute> attribute.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 In the following example, the <xref:System.Security.Permissions.SecurityAction> should be removed and the method marked with the <xref:System.Security.SecurityCriticalAttribute> attribute.  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]
