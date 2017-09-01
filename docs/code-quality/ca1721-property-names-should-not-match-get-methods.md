---
title: 'CA1721: Property names should not match get methods | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
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
ms.openlocfilehash: 7020896493b641f1b2aa4c77912636554441b3fe
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721: Property names should not match get methods
|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 The name of a public or protected member starts with 'Get' and otherwise matches the name of a public or protected property. For example, a type that contains a method that is named 'GetColor' and a property that is named 'Color' violates this rule.  
  
## <a name="rule-description"></a>Rule Description  
 Get methods and properties should have names that clearly distinguish their function.  
  
 Naming conventions provide a common look for libraries that target the common language runtime. This reduces the time that is required to learn a new software library, and increases customer confidence that the library was developed by someone who has expertise in developing managed code.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 Change the name so that it does not match the name of a method that is prefixed with 'Get'.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
> [!NOTE]
>  This warning may be excluded if the Get method is caused by implementing IExtenderProvider interface.  
  
## <a name="example"></a>Example  
 The following example contains a method and property that violate this rule.  
  
 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)] [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1024: Use properties where appropriate](../code-quality/ca1024-use-properties-where-appropriate.md)
