---
title: CA2222:不要降低繼承成員的可視性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: bdae21ec1a95cdc12cb6511a39f45e610e09b329
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031782"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222:不要降低繼承成員的可視性

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

非密封類型中的私用方法具有相同的基底類型中宣告的公用方法的簽章。 私用的方法不是最終的。

## <a name="rule-description"></a>規則描述

請勿變更繼承成員的存取修飾詞。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。 如果成員設為私用，而且未密封的型別，則繼承的類型可以呼叫繼承階層架構中的最後一個公用方法的實作。 如果您必須變更存取修飾詞，這個方法標記為 final，或其類型應該為密封，以避免方法遭到覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，會變更為非私用存取。 或者，如果您的程式語言支援，您可以進行方法最後一個。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反此規則的型別。

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]