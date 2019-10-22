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
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646304"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003：必須使用一般事件處理常式執行個體
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型包含會傳回 void 的委派，其簽章包含兩個參數（第一個是物件，第二個是可指派給 EventArgs 的類型），而包含的元件目標 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]。

## <a name="rule-description"></a>規則描述
 在 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 之前，為了將自訂資訊傳遞至事件處理常式，必須宣告新的委派，以指定衍生自 <xref:System.EventArgs?displayProperty=fullName> 類別的類別。 這在 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 中已不再成立，這會引進 <xref:System.EventHandler%601?displayProperty=fullName> 委派。 這個泛型委派可讓衍生自 <xref:System.EventArgs> 的任何類別與事件處理常式一起使用。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除委派，並使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派取代其使用方式。 如果委派是由 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 編譯器自動產生，請將事件宣告的語法變更為使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的委派。 在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 範例中，批註會說明如何修改範例以符合規則。 C#範例中的範例會顯示修改過的程式碼。

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>範例
 下列範例會移除上一個範例中符合規則的委派宣告，並使用 <xref:System.EventHandler%601?displayProperty=fullName> 委派取代 `ClassThatRaisesEvent` 和 `ClassThatHandlesEvent` 方法中的用法。

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
