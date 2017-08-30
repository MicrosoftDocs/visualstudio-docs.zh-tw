---
title: 'CA1804: Remove unused locals | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 18
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
ms.openlocfilehash: 59d25656b929c36978f609f8b97da506e582f6af
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Remove unused locals
|||  
|-|-|  
|TypeName|RemoveUnusedLocals|  
|CheckId|CA1804|  
|Category|Microsoft.Performance|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A method declares a local variable but does not use the variable except possibly as the recipient of an assignment statement. For analysis by this rule, the tested assembly must be built with debugging information and the associated program database (.pdb) file must be available.  
  
## <a name="rule-description"></a>Rule Description  
 Unused local variables and unnecessary assignments increase the size of an assembly and decrease performance.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, remove or use the local variable. Note that the C# compiler that is included with [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] removes unused local variables when the `optimize` option is enabled.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Suppress a warning from this rule if the variable was compiler emitted. It is also safe to suppress a warning from this rule, or to disable the rule, if performance and code maintenance are not primary concerns.  
  
## <a name="example"></a>Example  
 The following example shows several unused local variables.  
  
 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)] [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1809: Avoid excessive locals](../code-quality/ca1809-avoid-excessive-locals.md)  
  
 [CA1811: Avoid uncalled private code](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Avoid uninstantiated internal classes](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Review unused parameters](../code-quality/ca1801-review-unused-parameters.md)
