---
title: CA2241:必須提供格式化方法的正確引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f9f48f9cba146251aee1a58ffc7a3403ed899c4a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921493"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241:必須提供格式化方法的正確引數

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 `format`字串引數傳遞至方法，例如<xref:System.Console.WriteLine%2A>， <xref:System.Console.Write%2A>，或<xref:System.String.Format%2A?displayProperty=fullName>不包含對應至每個物件引數，或反之亦然的格式項目。

## <a name="rule-description"></a>規則描述
 這類方法的引數<xref:System.Console.WriteLine%2A>， <xref:System.Console.Write%2A>，並<xref:System.String.Format%2A>包含格式字串，後面接著數個<xref:System.Object?displayProperty=fullName>執行個體。 格式字串所組成的文字和內嵌的格式項目表單的 {索引 [，對齊] [: formatString]}。 'index' 是以零起始的整數，會指出需要格式化的物件。 如果物件在格式字串中沒有對應的索引，則會忽略的物件。 'Index' 所指定的物件不存在，如果<xref:System.FormatException?displayProperty=fullName>會在執行階段擲回。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，每個物件引數提供的格式項目，並提供每個格式項目之物件引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則。

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]