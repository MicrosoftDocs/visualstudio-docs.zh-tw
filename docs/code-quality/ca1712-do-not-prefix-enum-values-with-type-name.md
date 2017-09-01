---
title: 'CA1712: Do not prefix enum values with type name | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
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
ms.openlocfilehash: 771fe3536bbf9a47962f6219ce249a168b6b3215
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Do not prefix enum values with type name
|||  
|-|-|  
|TypeName|DoNotPrefixEnumValuesWithTypeName|  
|CheckId|CA1712|  
|Category|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 An enumeration contains a member whose name starts with the type name of the enumeration.  
  
## <a name="rule-description"></a>Rule Description  
 Names of enumeration members are not prefixed with the type name because type information is expected to be provided by development tools.  
  
 Naming conventions provide a common look for libraries that target the common language runtime. This reduces the time that is required for to learn a new software library, and increases customer confidence that the library was developed by someone who has expertise in developing managed code.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, remove the type name prefix from the enumeration member.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example shows an incorrectly named enumeration followed by the corrected version.  
  
 [!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)] [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)] [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1711: Identifiers should not have incorrect suffix](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
 [CA1027: Mark enums with FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Do not mark enums with FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Enum?displayProperty=fullName>
