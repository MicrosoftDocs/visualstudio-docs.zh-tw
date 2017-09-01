---
title: 'CA1819: Properties should not return arrays | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
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
ms.openlocfilehash: c8e145afcff87a0ac3250509758762db3d6e2de7
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: Properties should not return arrays
|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Category|Microsoft.Performance|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected property in a public type returns an array.  
  
## <a name="rule-description"></a>Rule Description  
 Arrays returned by properties are not write-protected, even if the property is read-only. To keep the array tamper-proof, the property must return a copy of the array. Typically, users will not understand the adverse performance implications of calling such a property. Specifically, they might use the property as an indexed property.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, either make the property a method or change the property to return a collection.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Attributes can contain properties that return arrays, but cannot contain properties that return collections. You can suppress a warning that is raised for a property of an attribute that is derived from the <xref:System.Attribute> class. Otherwise, do not suppress a warning from this rule.  
  
## <a name="example-violation"></a>Example Violation  
  
### <a name="description"></a>Description  
 The following example shows a property that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)] [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### <a name="comments"></a>Comments  
 To fix a violation of this rule, either make the property a method or change the property to return a collection instead of an array.  
  
## <a name="change-the-property-to-a-method-example"></a>Change the Property to a Method Example  
  
### <a name="description"></a>Description  
 The following example fixes the violation by changing the property to a method.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)] [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## <a name="return-a-collection-example"></a>Return a Collection Example  
  
### <a name="description"></a>Description  
 The following example fixes the violation by changing the property to return a  
  
 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)] [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## <a name="allowing-users-to-modify-a-property"></a>Allowing Users to Modify a Property  
  
### <a name="description"></a>Description  
 You might want to allow the consumer of the class to modify a property. The following example shows a read/write property that violates this rule.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)] [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### <a name="comments"></a>Comments  
 The following example fixes the violation by changing the property to return a <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>.  
  
### <a name="code"></a>Code  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)] [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1024: Use properties where appropriate](../code-quality/ca1024-use-properties-where-appropriate.md)
