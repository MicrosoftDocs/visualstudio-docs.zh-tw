---
title: CA1047：不要在密封類型中宣告 protected 成員
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a19e17c200f36d3edb1cadbab4d573f6a1d3cc0a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550056"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047：不要在密封類型中宣告 protected 成員

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|類別|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用類型是`sealed`(`NotInheritable` Visual basic 中)，並宣告受保護的成員或受保護的巢狀型別。 此規則不會報告的違規<xref:System.Object.Finalize%2A>必須遵循這個模式的方法。

## <a name="rule-description"></a>規則描述
 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，您無法繼承自密封型別，也就是說，受保護的方法，密封類型上的無法呼叫。

 C# 編譯器會發出這項錯誤的警告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更成員的存取層級設為私用，或讓類型成為可繼承。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 類型在目前的狀態可能會造成維護問題並不提供任何好處。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別。

 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]