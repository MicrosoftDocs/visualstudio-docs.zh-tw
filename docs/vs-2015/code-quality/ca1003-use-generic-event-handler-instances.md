---
title: CA1003 必須：使用一般事件處理常式實例 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539902"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：使用一般事件處理常式執行個體
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別包含傳回 void 的委派，其簽章包含兩個參數 (第一個物件，第二個則是可指派給 EventArgs) 的型別，以及包含元件目標 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。

## <a name="rule-description"></a>規則描述
 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]在之前，為了將自訂資訊傳遞至事件處理常式，必須宣告新的委派，以指定衍生自類別的類別 <xref:System.EventArgs?displayProperty=fullName> 。 這在引進委派的中已不再成立 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] <xref:System.EventHandler%601?displayProperty=fullName> 。 這個泛型委派可讓任何衍生自的類別 <xref:System.EventArgs> 與事件處理常式一起使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除委派，並使用委派取代其使用方式 <xref:System.EventHandler%601?displayProperty=fullName> 。 如果編譯器會自動產生委派 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，請將事件宣告的語法變更為使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的委派。 在此 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 範例中，批註會描述如何修改範例以滿足規則。 針對 c # 範例，下列範例會顯示已修改的程式碼。

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>範例
 下列範例會移除上一個範例中的委派宣告（滿足規則），並 `ClassThatRaisesEvent` 使用委派取代和方法中的使用 `ClassThatHandlesEvent` <xref:System.EventHandler%601?displayProperty=fullName> 。

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007:建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
