---
title: 'CA2215: Dispose methods should call base class dispose | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
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
ms.openlocfilehash: 2fc05a4489fbd8b4d30cb3e9c3e9c0e86c2c26a5
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Dispose methods should call base class dispose
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 A type that implements <xref:System.IDisposable?displayProperty=fullName> inherits from a type that also implements <xref:System.IDisposable>. The <xref:System.IDisposable.Dispose%2A> method of the inheriting type does not call the <xref:System.IDisposable.Dispose%2A> method of the parent type.  
  
## <a name="rule-description"></a>Rule Description  
 If a type inherits from a disposable type, it must call the <xref:System.IDisposable.Dispose%2A> method of the base type from within its own <xref:System.IDisposable.Dispose%2A> method. Calling the base type method Dispose ensures that any resources created by the base type are released.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, call `base`.<xref:System.IDisposable.Dispose%2A> in your <xref:System.IDisposable.Dispose%2A> method.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule if the call to `base`.<xref:System.IDisposable.Dispose%2A> occurs at a deeper calling level than the rule checks.  
  
## <a name="example"></a>Example  
 The following example shows a type `TypeA` that implements <xref:System.IDisposable>.  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>Example  
 The following example shows a type `TypeB` that inherits from type `TypeA` and correctly calls its <xref:System.IDisposable.Dispose%2A> method.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>See Also  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose Pattern](/dotnet/standard/design-guidelines/dispose-pattern)
