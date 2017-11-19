---
title: "CA1000： 不要在泛型類型上宣告靜態成員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24d46fc6817f4d13ea5502ada707e2abbcdbfda9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000：不要在泛型類型上宣告靜態成員
|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 外部可見的泛型型別包含`static`(`Shared`在 Visual Basic 中) 成員。  
  
## <a name="rule-description"></a>規則描述  
 當`static`呼叫泛型類型的成員，必須指定型別引數的類型。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 兩種情況中指定的型別引數的語法是不同且容易混淆，如下列的呼叫所示：  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```csharp  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 一般而言，這兩個先前的宣告應該避免這樣呼叫成員時，必須指定沒有型別引數。 這會導致語法中的泛型與非泛型語法並無不同，呼叫成員。 如需詳細資訊，請參閱[CA1004： 泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請移除靜態成員或將它變更為執行個體成員。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 提供了易於了解和使用的語法中的泛型減少的時間，需要了解並增加新的媒體櫃的採用率。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>另請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)