---
title: 'CA1032: Implement standard exception constructors | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
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
ms.openlocfilehash: 42fd1ecaab987ba35fe180c99a6f54f48a30067c
ms.contentlocale: zh-tw
ms.lasthandoff: 08/30/2017

---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Implement standard exception constructors
|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Category|Microsoft.Design|  
|Breaking Change|Non-breaking|  
  
## <a name="cause"></a>Cause  
 A type extends <xref:System.Exception?displayProperty=fullName> and does not declare all the required constructors.  
  
## <a name="rule-description"></a>Rule Description  
 Exception types must implement the following constructors:  
  
-   public NewException()  
  
-   public NewException(string)  
  
-   public NewException(string, Exception)  
  
-   protected or private NewException(SerializationInfo, StreamingContext)  
  
 Failure to provide the full set of constructors can make it difficult to correctly handle exceptions. For example, the constructor that has the signature `NewException(string, Exception)` is used to create exceptions that are caused by other exceptions. Without this constructor you cannot create and throw an instance of your custom exception that contains an inner (nested) exception, which is what managed code should do in such a situation. The first three exception constructors are public by convention. The fourth constructor is protected in unsealed classes, and private in sealed classes. For more information, see [CA2229: Implement serialization constructors](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, add the missing constructors to the exception, and make sure that they have the correct accessibility.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 It is safe to suppress a warning from this rule when the violation is caused by using a different access level for the public constructors.  
  
## <a name="example"></a>Example  
 The following example contains an exception type that violates this rule and an exception type that is correctly implemented.  
  
 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]
