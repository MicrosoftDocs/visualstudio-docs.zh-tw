---
title: 'CA2229: Implement serialization constructors | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
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
ms.openlocfilehash: d604f1d7d1acdbf72681378dd5780d5e76c6aec6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implement serialization constructors
|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Category|Microsoft.Usage|  
|Breaking Change|Non Breaking|  
  
## <a name="cause"></a>Cause  
 The type implements the <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interface, is not a delegate or interface, and one of the following conditions is true:  
  
-   The type does not have a constructor that takes a <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> object and a <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> object (the signature of the serialization constructor).  
  
-   The type is unsealed and the access modifier for its serialization constructor is not protected (family).  
  
-   The type is sealed and the access modifier for its serialization constructor is not private.  
  
## <a name="rule-description"></a>Rule Description  
 This rule is relevant for types that support custom serialization. A type supports custom serialization if it implements the <xref:System.Runtime.Serialization.ISerializable> interface. The serialization constructor is required to deserialize, or re-create objects that have been serialized using the <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> method.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, implement the serialization constructor. For a sealed class, make the constructor private; otherwise, make it protected.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a violation of the rule. The type will not be deserializable, and will not function in many scenarios.  
  
## <a name="example"></a>Example  
 The following example shows a type that satisfies the rule.  
  
 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA2237: Mark ISerializable types with SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
