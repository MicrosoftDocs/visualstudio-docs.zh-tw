---
title: 'CA1415: Declare P-Invokes correctly | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
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
ms.openlocfilehash: 2e19d4a786bb58ac6fac55ebcb977be8c330a081
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declare P/Invokes correctly
|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Non-breaking - If the P/Invoke that declares the parameter cannot be seen outside the assembly. Breaking - If the P/Invoke that declares the parameter can be seen outside the assembly.|  
  
## <a name="cause"></a>Cause  
 A platform invoke method is incorrectly declared.  
  
## <a name="rule-description"></a>Rule Description  
 A platform invoke method accesses unmanaged code and is defined by using the `Declare` keyword in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] or the <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Currently, this rule looks for platform invoke method declarations that target Win32 functions that have a pointer to an OVERLAPPED structure parameter and the corresponding managed parameter is not a pointer to a <xref:System.Threading.NativeOverlapped?displayProperty=fullName> structure.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, correctly declare the platform invoke method.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows platform invoke methods that violate the rule and satisfy the rule.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>See Also  
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index)
