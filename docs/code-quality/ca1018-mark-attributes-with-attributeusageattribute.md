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
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306129"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:必須以 AttributeUsageAttribute 標記屬性

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
@No__t-0 屬性不存在於自訂屬性上。

## <a name="rule-description"></a>規則描述
當您定義自訂屬性時，請使用 <xref:System.AttributeUsageAttribute> 來標示它，以指示原始程式碼中可套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義一個屬性來識別負責維護和增強程式庫中每個類型的人員，而且該責任一律會在類型層級指派。 在此情況下，編譯器應該啟用類別、列舉和介面上的屬性，但不應在方法、事件或屬性上啟用它。 組織原則和程式會決定是否應該在元件上啟用屬性。

@No__t-0 列舉會定義您可以為自訂屬性指定的目標。 如果您省略 <xref:System.AttributeUsageAttribute>，則自訂屬性將對所有目標有效，如 <xref:System.AttributeTargets> 列舉的 `All` 值所定義。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請使用 <xref:System.AttributeUsageAttribute> 來指定屬性的目標。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
您應該修正此規則的違規，而不是排除訊息。 即使屬性繼承 <xref:System.AttributeUsageAttribute>，該屬性也應該存在，以簡化程式碼維護。

## <a name="example"></a>範例
下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute` 不正確地省略 <xref:System.AttributeUsageAttribute> 語句，而 `GoodCodeMaintainerAttribute` 會正確地執行本節稍早所述的屬性。 請注意，設計規則 [CA1019 需要屬性 `DeveloperName`：定義屬性引數 @ no__t-0 的存取子，並納入完整性。

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1019：定義屬性引數的存取子 @ no__t-0

[CA1813：避免未密封的屬性 @ no__t-0

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)