---
title: CA1047:不要在密封類型中宣告 protected 成員
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3114ea004c425567ae479343e0449d2cbc3aa669
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235694"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047:不要在密封類型中宣告 protected 成員

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|分類|Microsoft.Design|
|重大變更|不中斷|

## <a name="cause"></a>原因
公用類型為（ `sealed` `NotInheritable`在 Visual basic 中為），並宣告受保護的成員或受保護的巢狀型別。 此規則不會針對<xref:System.Object.Finalize%2A>必須遵循此模式的方法報告違規。

## <a name="rule-description"></a>規則描述
類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，您無法從密封類型繼承，這表示不能呼叫密封類型上的受保護方法。

C#編譯器會發出此錯誤的警告。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將成員的存取層級變更為 [私用]，或將類型設為 [可繼承]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 讓類型處於目前狀態可能會造成維護問題，而且不會提供任何好處。

## <a name="example"></a>範例
下列範例顯示違反此規則的類型。

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]