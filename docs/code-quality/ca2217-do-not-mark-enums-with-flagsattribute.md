---
title: CA2217:不要以 FlagsAttribute 標記列舉
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8afe63de8630b3fa7466e8c0784c26ba00bb1ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852475"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:不要以 FlagsAttribute 標記列舉

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

外部可見的列舉型別會標示<xref:System.FlagsAttribute>，和它有一個或多個值不是兩種或多種其他的次方列舉型別上定義的值。

## <a name="rule-description"></a>規則描述

列舉型別應該有<xref:System.FlagsAttribute>目前只有在列舉中定義的每個值是兩個或組合的乘冪定義值。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請移除<xref:System.FlagsAttribute>列舉中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example-that-should-not-have-the-attribute"></a>不應具有屬性的範例

下列範例示範列舉型別， `Color`，其中包含的值是 3。 3 不是兩個或任何已定義的值組合的乘冪。 `Color`列舉型別不應該以標示<xref:System.FlagsAttribute>。

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>應具有屬性的範例

下列範例示範一個列舉，而`Days`，符合的需求標示<xref:System.FlagsAttribute>。

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>相關的規則

[CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>
