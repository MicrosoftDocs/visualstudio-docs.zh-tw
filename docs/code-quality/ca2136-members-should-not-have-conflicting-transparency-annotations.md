---
title: 'CA2136: Members should not have conflicting transparency annotations | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
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
ms.openlocfilehash: 8196f6ad5b0ff84182d31d2286b02a2b557783f9
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Members should not have conflicting transparency annotations
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 This rule fires when a type member is marked with a <xref:System.Security> security attribute that has a different transparency than the security attribute of a container of the member.  
  
## <a name="rule-description"></a>Rule Description  
 Transparency attributes are applied from code elements of larger scope to elements of smaller scope. The transparency attributes of code elements with larger scope take precedence over transparency attributes of code elements that are contained in the first element. For example, a class that is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute cannot contain a method that is marked with the <xref:System.Security.SecuritySafeCriticalAttribute> attribute.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix this violation, remove the security attribute from the code element that has lower scope, or change its attribute to be the same as the containing code element.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress warnings from this rule.  
  
## <a name="example"></a>Example  
 In the following example, a method is marked with the <xref:System.Security.SecuritySafeCriticalAttribute> attribute and it is a member of a class that is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute. The security safe attribute should be removed.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]
