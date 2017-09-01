---
title: 'CA2133: Delegates must bind to methods with consistent transparency | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
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
ms.openlocfilehash: 473dbf2d6373c59c693a91db804897bfe73b5300
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegates must bind to methods with consistent transparency
|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
> [!NOTE]
>  This warning is only applied to code that is running the CoreCLR (the version of the CLR that is specific to Silverlight Web applications).  
  
## <a name="cause"></a>Cause  
 This warning fires on a method that binds a delegate that is marked with the <xref:System.Security.SecurityCriticalAttribute> to a method that is transparent or that is marked with the <xref:System.Security.SecuritySafeCriticalAttribute>. The warning also fires a method that binds a delegate that is transparent or safe-critical to a critical method.  
  
## <a name="rule-description"></a>Rule Description  
 Delegate types and the methods that they bind to must have consistent transparency. Transparent and safe-critical delegates may only bind to other transparent or safe-critical methods. Similarly, critical delegates may only bind to critical methods. These binding rules ensure that the only code that can invoke a method via a delegate could have also invoked the same method directly. For example, binding rules prevent transparent code from calling critical code directly via a transparent delegate.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this warning, change the transparency of the delegate or of the method that it binds so that the transparency of the two are equivalent.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]
