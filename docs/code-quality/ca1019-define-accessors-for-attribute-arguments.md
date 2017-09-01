---
title: 'CA1019: Define accessors for attribute arguments | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
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
ms.openlocfilehash: c54f96f07e1c02cfab07a63504cd44a7884a3fad
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Define accessors for attribute arguments
|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|Category|Microsoft.Design|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 In its constructor, an attribute defines arguments that do not have corresponding properties.  
  
## <a name="rule-description"></a>Rule Description  
 Attributes can define mandatory arguments that must be specified when you apply the attribute to a target. These are also known as positional arguments because they are supplied to attribute constructors as positional parameters. For every mandatory argument, the attribute should also provide a corresponding read-only property so that the value of the argument can be retrieved at execution time. This rule checks that for each constructor parameter, you have defined the corresponding property.  
  
 Attributes can also define optional arguments, which are also known as named arguments. These arguments are supplied to attribute constructors by name and should have a corresponding read/write property.  
  
 For mandatory and optional arguments, the corresponding properties and constructor parameters should use the same name but different casing. Properties use Pascal casing, and parameters use camel casing.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, add a read-only property for each constructor parameter that does not have one.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Suppress a warning from this rule if you do not want the value of the mandatory argument to be retrievable.  
  
## <a name="custom-attributes-example"></a>Custom Attributes Example  
  
### <a name="description"></a>Description  
 The following example shows two attributes that define a mandatory (positional) parameter. The first implementation of the attribute is incorrectly defined. The second implementation is correct.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)] [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## <a name="positional-and-named-arguments"></a>Positional and Named Arguments  
  
### <a name="description"></a>Description  
 Positional and named arguments make to clear to consumers of your library which arguments are mandatory for the attribute and which arguments are optional.  
  
 The following example shows an implementation of an attribute that has both positional and named arguments.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### <a name="comments"></a>Comments  
 The following example shows how to apply the custom attribute to two properties.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1813: Avoid unsealed attributes](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>See Also  
 [Attributes](/dotnet/standard/design-guidelines/attributes)
