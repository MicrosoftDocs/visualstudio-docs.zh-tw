---
title: 'CA2111: Pointers should not be visible | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
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
ms.openlocfilehash: 9cc87d45fe19ec583499f918cb1e50528c418925
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111: Pointers should not be visible
|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|CheckId|CA2111|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected <xref:System.IntPtr?displayProperty=fullName> or <xref:System.UIntPtr?displayProperty=fullName> field is not read-only.  
  
## <a name="rule-description"></a>Rule Description  
 <xref:System.IntPtr> and <xref:System.UIntPtr> are pointer types that are used to access unmanaged memory. If a pointer is not private, internal, or read-only, malicious code can change the value of the pointer, potentially allowing access to arbitrary locations in memory or causing application or system failures.  
  
 If you intend to secure access to the type that contains the pointer field, see [CA2112: Secured types should not expose fields](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 Secure the pointer by making it read-only, internal, or private.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Suppress a warning from this rule if you do not rely on the value of the pointer.  
  
## <a name="example"></a>Example  
 The following code shows pointers that violate and satisfy the rule. Notice that the non-private pointers also violate the rule [CA1051: Do not declare visible instance fields](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2112: Secured types should not expose fields](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: Do not declare visible instance fields](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>
