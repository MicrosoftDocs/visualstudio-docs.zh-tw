---
title: CA1007： 使用泛型適當 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 31f15bfc62943bb71acfba24432560facce9d636
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861718"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007：建議在適當時使用泛型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的方法包含類型的參考參數<xref:System.Object?displayProperty=fullName>，和包含的組件目標[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]。

## <a name="rule-description"></a>規則描述
 參考參數會使用已修改的參數`ref`(`ByRef`在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 關鍵字。 提供做為參考參數的引數類型必須完全符合參考參數型別。 若要使用衍生自參考的參數類型的類型，類型必須先轉換並指派給變數的參考參數的類型。 使用泛型的方法可讓所有的類型，受限於條件約束，以傳遞至方法，而不先將轉型為參考參數型別類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，使方法成為泛型，並取代<xref:System.Object>所使用的型別參數的參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會實作為泛型和非泛型方法的一般用途的交換常式。 請注意，字串會交換使用相較於非泛型方法的泛型方法的效率。

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>另請參閱
 [泛型](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



