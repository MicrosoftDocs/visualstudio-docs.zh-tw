---
title: "CA1006： 不要巢狀成員簽章中的泛型類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2ec28ce2cfe1e8c0de622a0f35d37ddd82e1be7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006：不要在成員簽章中巢狀化泛型類型
|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 外部可見成員的簽章含有巢狀的型別引數。  
  
## <a name="rule-description"></a>規則描述  
 巢狀類型引數就是也是泛型類型的類型引數。 若要呼叫其簽章含有巢狀類型引數的成員，則使用者必須具現化 (Instantiate) 一個泛型類型，並將這個類型傳遞給第二個泛型類型的建構函式。 必要程序及語法十分複雜，且應予以避免。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更設計，以移除巢狀型別引數。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 提供了易於了解和使用的語法中的泛型減少的時間，需要了解並增加新的媒體櫃的採用率。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的方法，才能呼叫違規方法的語法。  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>另請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)