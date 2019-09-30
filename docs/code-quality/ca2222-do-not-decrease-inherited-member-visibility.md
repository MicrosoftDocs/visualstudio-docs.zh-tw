---
title: CA2222:不要降低繼承成員的可視性
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230987"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222:不要降低繼承成員的可視性

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

未密封類型中的私用方法，其簽章與基底類型中宣告的公用方法完全相同。 私用方法不是最終的。

## <a name="rule-description"></a>規則描述

請勿變更繼承成員的存取修飾詞。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。 如果將成員設為私用，而且該類型未密封，繼承類型就可以在繼承階層架構中呼叫方法的最後一個公用實體系。 如果您必須變更存取修飾詞，則應該將方法標示為 final，或其類型應為密封，以防止覆寫方法。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將存取權變更為非私用。 或者，如果您的程式設計語言支援它，您可以將方法設為最終。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反此規則的類型。

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]