---
title: CA2242:必須正確測試 NaN
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237846"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242:必須正確測試 NaN

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
運算式會針對<xref:System.Single.NaN?displayProperty=fullName>或<xref:System.Double.NaN?displayProperty=fullName>測試值。

## <a name="rule-description"></a>規則描述
 <xref:System.Double.NaN?displayProperty=fullName>表示非數位的，未定義算數運算時的結果。 測試值是否相等並<xref:System.Double.NaN?displayProperty=fullName> `false`一律傳回的任何運算式。 測試值是否不相等，且<xref:System.Double.NaN?displayProperty=fullName> `true`一律會傳回的任何運算式。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，並準確判斷某個值是否<xref:System.Double.NaN?displayProperty=fullName>代表， <xref:System.Single.IsNaN%2A?displayProperty=fullName>請<xref:System.Double.IsNaN%2A?displayProperty=fullName>使用或來測試值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示兩個不正確測試值<xref:System.Double.NaN?displayProperty=fullName>的運算式，以及正確地用<xref:System.Double.IsNaN%2A?displayProperty=fullName>來測試值的運算式。

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]