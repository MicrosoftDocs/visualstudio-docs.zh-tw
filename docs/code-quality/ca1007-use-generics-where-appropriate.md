---
title: CA1007：建議在適當時使用泛型
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4aa1bb976cdbcc3d3b97e463ce0076bccdd26ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007：建議在適當時使用泛型
|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的方法包含類型的參考參數<xref:System.Object?displayProperty=fullName>，和包含組件目標[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]。

## <a name="rule-description"></a>規則描述
 參考參數是參數，利用修改`ref`(`ByRef`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 關鍵字。 提供做為參考參數的引數類型必須完全符合參考參數類型。 若要使用衍生自參考的參數類型的類型，類型必須先轉換而指派給參考參數類型的變數。 使用泛型的方法可讓所有類型，受限於條件約束，而不先將轉型為參考參數類型的型別傳遞至方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將方法設為泛型，並取代<xref:System.Object>使用型別參數的參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會實作為泛型和非泛型方法的一般用途的交換常式。 請注意，字串會交換使用相較於非泛型方法之泛型方法的效率。

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>另請參閱
 [泛型](/dotnet/csharp/programming-guide/generics/index)