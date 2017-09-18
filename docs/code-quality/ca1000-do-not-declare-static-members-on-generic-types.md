---
title: "CA1000：不要在泛型類型上宣告靜態成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1000：不要在泛型類型上宣告靜態成員
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 外部可見的泛型型別包含 `static` \(在 Visual Basic 中為 `Shared`\) 成員。  
  
## 規則描述  
 呼叫泛型型別的 `static` 成員時，必須為型別指定型別引數。  呼叫不支援介面的泛型執行個體 \(Instance\) 成員時，必須為成員指定型別引數。  在上述兩種情況下指定型別引數的語法不同且容易混淆，如下列呼叫所示範：  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 一般而言，這兩者都應該避免先宣告，如此在呼叫成員時才不必指定型別引數。  呼叫泛型成員的語法結果會與呼叫非泛型的語法結果相同。  如需詳細資訊，請參閱[CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請移除靜態成員，或將它變更為執行個體成員。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  使用易於了解和使用的語法提供泛型，以便減少學習所需的時間，並增加新程式庫的採用率。  
  
## 相關規則  
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)