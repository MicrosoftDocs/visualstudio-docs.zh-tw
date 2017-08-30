---
title: 'CA1708: Identifiers should differ by more than case | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
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
ms.openlocfilehash: d935ed7e683747bdbbbc1a24f0ccbee602d0b072
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identifiers should differ by more than case
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 The names of two types, members, parameters, or fully qualified namespaces are identical when they are converted to lowercase.  
  
## <a name="rule-description"></a>Rule Description  
 Identifiers for namespaces, types, members, and parameters cannot differ only by case because languages that target the common language runtime are not required to be case-sensitive. For example, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] is a widely used case-insensitive language.  
  
 This rule fires on publicly visible members only.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 Select a name that is unique when it is compared to other identifiers in a case-insensitive manner.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule. The library might not be usable in all available languages in the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="example-of-a-violation"></a>Example of a Violation  
 The following example demonstrates a violation of this rule.  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1709: Identifiers should be cased correctly](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
