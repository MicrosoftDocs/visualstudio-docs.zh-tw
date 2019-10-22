---
title: CA1047：不要在密封類型中宣告 protected 成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebc6732e559b70e753a44b14cf45b7de9fc150d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668175"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047：不要在密封類型中宣告 protected 成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用類型為 `sealed` （在 Visual basic 中為 `NotInheritable`），並宣告受保護的成員或受保護的巢狀型別。 此規則不會報告違反 <xref:System.Object.Finalize%2A> 方法，這必須遵循此模式。

## <a name="rule-description"></a>規則描述
 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，您無法從密封類型繼承，這表示不能呼叫密封類型上的受保護方法。

 C#編譯器會發出此錯誤的警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將成員的存取層級變更為 [私用]，或將類型設為 [可繼承]。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 讓類型處於目前狀態可能會造成維護問題，而且不會提供任何好處。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型。

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
