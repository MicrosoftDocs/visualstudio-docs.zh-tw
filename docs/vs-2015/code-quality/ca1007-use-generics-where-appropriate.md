---
title: CA1007 建議：適當時使用泛型 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4ee33305c1ae0f15e5d8f390a4b65d62c87b6904
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547936"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007:建議在適當時使用泛型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的方法包含型別的參考參數 <xref:System.Object?displayProperty=fullName> ，以及包含元件目標 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。

## <a name="rule-description"></a>規則描述
 參考參數是使用 `ref` （ `ByRef` in）關鍵字來修改的參數 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。 為參考參數提供的引數類型必須完全符合參考參數類型。 若要使用衍生自參考參數類型的類型，必須先轉換類型，並將其指派給參考參數類型的變數。 使用泛型方法可讓所有類型（受限於條件約束）傳遞至方法，而不需要先將類型轉換為參考參數類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將方法設為泛型，並 <xref:System.Object> 使用型別參數來取代參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示同時實作為非泛型和泛型方法的一般用途交換常式。 請注意，相較于非泛型方法，使用泛型方法來交換字串的效率如何。

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>另請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
