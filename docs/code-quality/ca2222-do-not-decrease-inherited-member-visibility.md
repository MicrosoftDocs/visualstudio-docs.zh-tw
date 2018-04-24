---
title: CA2222：請勿降低繼承成員的可視性
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8730789ef9f905def64c17081eb44113241282
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222：請勿降低繼承成員的可視性
|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非密封類型中的私用的方法有相同的基底類型中宣告的公用方法的簽章。 私用的方法不是最後一個。

## <a name="rule-description"></a>規則描述
 您不得變更繼承成員的存取修飾詞 (Modifier)。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。 如果變成私用成員，而非密封類型，則繼承的類型可以呼叫階層架構中的最後一個公用實作的方法。 如果您必須變更存取修飾詞，方法應該標記為 final 或它的類型應該為密封，以避免覆寫此方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更為非私用存取。 或者，如果您的程式語言支援它，您可以將方法設最後。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]