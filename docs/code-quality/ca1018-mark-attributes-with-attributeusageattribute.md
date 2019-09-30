---
title: CA1018:必須以 AttributeUsageAttribute 標記屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a1ed8610ce84279f5fde3b802d976a3e766d99
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236244"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:必須以 AttributeUsageAttribute 標記屬性

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
<xref:System.AttributeUsageAttribute?displayProperty=fullName>屬性不存在於自訂屬性上。

## <a name="rule-description"></a>規則描述
當您定義自訂屬性時，請使用<xref:System.AttributeUsageAttribute>加以標記，以指出原始程式碼中可套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義一個屬性來識別負責維護和增強程式庫中每個類型的人員，而且該責任一律會在類型層級指派。 在此情況下，編譯器應該啟用類別、列舉和介面上的屬性，但不應在方法、事件或屬性上啟用它。 組織原則和程式會決定是否應該在元件上啟用屬性。

<xref:System.AttributeTargets?displayProperty=fullName>列舉會定義您可以為自訂屬性指定的目標。 如果您省略<xref:System.AttributeUsageAttribute>，您的自訂屬性將對所有目標有效，如<xref:System.AttributeTargets>列舉值`All`所定義。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請使用<xref:System.AttributeUsageAttribute>來指定屬性的目標。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
您應該修正此規則的違規，而不是排除訊息。 即使屬性繼承<xref:System.AttributeUsageAttribute>，屬性也應該存在，以簡化程式碼維護。

## <a name="example"></a>範例
下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute`不正確地<xref:System.AttributeUsageAttribute>省略語句， `GoodCodeMaintainerAttribute`並正確地執行本節稍早所述的屬性。 請注意，[ `DeveloperName`設計規則[] ca1019 必須需要屬性：定義屬性引數](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)的存取子，並納入完整性。

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1019 必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813避免未密封的屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)