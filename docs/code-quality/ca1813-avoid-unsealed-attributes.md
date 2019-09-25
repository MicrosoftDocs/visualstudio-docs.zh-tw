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
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233589"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813:避免使用非密封屬性

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|分類|Microsoft.Performance|
|重大變更|中斷|

## <a name="cause"></a>原因

公用型別繼承自<xref:System.Attribute?displayProperty=fullName>、不是抽象的，而且不是密封`NotInheritable`的（在 Visual Basic 中）。

## <a name="rule-description"></a>規則描述

.NET 提供用來抓取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構。 例如， <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>搜尋指定的屬性類型或任何延伸指定屬性類型的屬性類型。 密封屬性可避免透過繼承階層進行搜尋，並且可以改善效能。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請密封屬性類型，或將它設為抽象。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則的警告。 只有在您要定義屬性階層，而且無法密封屬性或使其成為抽象時，才會隱藏。

## <a name="example"></a>範例

下列範例顯示符合此規則的自訂屬性。

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>相關規則

- [CA1019 必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018:以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)