---
title: CA2242 必須：正確地測試 NaN |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672013"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242：必須正確測試 NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 運算式會針對 <xref:System.Single.NaN?displayProperty=fullName> 或 <xref:System.Double.NaN?displayProperty=fullName> 測試值。

## <a name="rule-description"></a>規則描述
 當算數運算未定義時，<xref:System.Double.NaN?displayProperty=fullName>，代表不是數位的結果。 測試值和 <xref:System.Double.NaN?displayProperty=fullName> 之間是否相等的任何運算式，一律會傳回 `false`。 測試值和 <xref:System.Double.NaN?displayProperty=fullName> 之間不相等的任何運算式，一律會傳回 `true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，並準確判斷某個值是否代表 <xref:System.Double.NaN?displayProperty=fullName>，請使用 <xref:System.Single.IsNaN%2A?displayProperty=fullName> 或 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 來測試值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個不正確地針對 <xref:System.Double.NaN?displayProperty=fullName> 測試值的運算式，以及正確使用 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 來測試值的運算式。

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
