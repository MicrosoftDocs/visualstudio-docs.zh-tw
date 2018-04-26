---
title: CA2242：必須正確測試 NaN
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164072203a4dc4dc9d0351f6c45f425260078848
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242：必須正確測試 NaN
|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 運算式針對測試值<xref:System.Single.NaN?displayProperty=fullName>或<xref:System.Double.NaN?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 <xref:System.Double.NaN?displayProperty=fullName>其代表不是數字，結果是未定義的算術運算時。 測試值是否相等的任何運算式和<xref:System.Double.NaN?displayProperty=fullName>一律會傳回`false`。 測試是否不相等的值之間的任何運算式和<xref:System.Double.NaN?displayProperty=fullName>一律會傳回`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形並準確地判斷值是否代表<xref:System.Double.NaN?displayProperty=fullName>，使用<xref:System.Single.IsNaN%2A?displayProperty=fullName>或<xref:System.Double.IsNaN%2A?displayProperty=fullName>即可測試值。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示不正確地測試 根據值的兩個運算式<xref:System.Double.NaN?displayProperty=fullName>正確使用的運算式和<xref:System.Double.IsNaN%2A?displayProperty=fullName>即可測試值。

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]