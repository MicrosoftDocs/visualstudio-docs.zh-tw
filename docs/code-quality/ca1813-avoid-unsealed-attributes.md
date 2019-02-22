---
title: CA1813:避免使用非密封屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4d7236b77a7dd0a81f8a7846c0eba28e3b520cdd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931815"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813:避免使用非密封屬性

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因

公用類型繼承自<xref:System.Attribute?displayProperty=fullName>、 不是抽象的而且不密封 (`NotInheritable` Visual Basic 中)。

## <a name="rule-description"></a>規則描述

.NET Framework 類別庫會提供方法來擷取自訂屬性。 根據預設，這些方法會搜尋屬性繼承階層架構。 比方說，<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>搜尋指定的屬性型別或任何延伸指定的屬性類型的屬性類型。 密封屬性排除整個繼承階層架構中，搜尋，並可改善效能。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請密封屬性類型，或將它設為抽象。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告。 只有在您要定義屬性階層隱藏，而且無法密封屬性或將它設為抽象。

## <a name="example"></a>範例

下列範例顯示自訂屬性，以符合這項規則。

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1019： 必須定義存取子屬性引數](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018:以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)