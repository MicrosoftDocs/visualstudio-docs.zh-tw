---
title: 'CA2149: Transparent methods must not call into native code | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
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
ms.openlocfilehash: 71ec50be4ff379c67cc775d61903a37e8bd2a773
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Transparent methods must not call into native code
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A method calls a native function through a method stub such as P/Invoke.  
  
## <a name="rule-description"></a>Rule Description  
 This rule fires on any transparent method which calls directly into native code, for example, through a P/Invoke. Violations of this rule lead to a <xref:System.MethodAccessException> in the level 2 transparency model, and a full demand for <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> in the level 1 transparency model.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, mark the method that calls the native code with the <xref:System.Security.SecurityCriticalAttribute> or <xref:System.Security.SecuritySafeCriticalAttribute> attribute.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]
