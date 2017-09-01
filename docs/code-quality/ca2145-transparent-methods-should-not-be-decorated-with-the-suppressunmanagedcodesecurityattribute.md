---
title: 'CA2145: Transparent methods should not be decorated with the SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
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
ms.openlocfilehash: 119d4a5f0d27953f66fb64394bc35fa606b9bc7d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Transparent methods should not be decorated with the SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A transparent method, a method that is marked with the <xref:System.Security.SecuritySafeCriticalAttribute> method, or a type that contains a method is marked with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute.  
  
## <a name="rule-description"></a>Rule Description  
 Methods decorated with the <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribute have an implicit LinkDemand placed upon any method that calls it. This LinkDemand requires that the calling code be security critical. Marking the method that uses SuppressUnmanagedCodeSecurity with the <xref:System.Security.SecurityCriticalAttribute> attribute makes this requirement more obvious for callers of the method.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, mark the method or type with the <xref:System.Security.SecurityCriticalAttribute> attribute.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>Comments
