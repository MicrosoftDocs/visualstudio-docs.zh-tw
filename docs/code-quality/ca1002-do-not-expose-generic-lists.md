---
title: "CA1002： 不要公開泛型清單 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 08092243699e58bd6bc4d737d31c60e5b3c3dd0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002：不要公開泛型清單
|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|CheckId|CA1002|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 包含的類型是外部可見成員<xref:System.Collections.Generic.List%601?displayProperty=fullName>傳回型別，<xref:System.Collections.Generic.List%601?displayProperty=fullName>類型或簽章包含<xref:System.Collections.Generic.List%601?displayProperty=fullName>參數。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>已針對效能與非繼承所設計的泛型集合。 <xref:System.Collections.Generic.List%601?displayProperty=fullName>不包含可讓您更輕鬆地變更繼承的類別行為的虛擬成員。 下列的泛型集合專為繼承，且應該公開 (expose) 而不是<xref:System.Collections.Generic.List%601?displayProperty=fullName>。  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更<xref:System.Collections.Generic.List%601?displayProperty=fullName>是專為繼承所設計的泛型集合的其中一個型別。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告，除非會引發下列警告的組件不是可重複使用程式庫。 例如，則可放心將可隱藏這個警告，效能微調應用程式中的已使用的泛型清單所獲得效能優勢。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>另請參閱  
 [泛型](/dotnet/csharp/programming-guide/generics/index)