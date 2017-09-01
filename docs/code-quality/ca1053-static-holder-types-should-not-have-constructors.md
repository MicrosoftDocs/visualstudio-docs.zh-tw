---
title: 'CA1053: Static holder types should not have constructors | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
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
ms.openlocfilehash: 26a8887ff5604028d3028749230151d5b0555827
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053: Static holder types should not have constructors
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Category|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or nested public type declares only static members and has a public or protected default constructor.  
  
## <a name="rule-description"></a>Rule Description  
 The constructor is unnecessary because calling static members does not require an instance of the type. Also, because the type does not have non-static members, creating an instance does not provide access to any of the type's members.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, remove the default constructor or make it private.  
  
> [!NOTE]
>  Some compilers automatically create a public default constructor if the type does not define any constructors. If this is the case with your type, add a private default constructor to eliminate the violation.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule. The presence of the constructor suggests that the type is not a static type.  
  
## <a name="example"></a>Example  
 The following example shows a type that violates this rule. Notice that there is no default constructor in the source code. When this code is compiled into an assembly, the C# compiler will insert a default constructor, which will violate this rule. To correct this, declare a private constructor.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]
