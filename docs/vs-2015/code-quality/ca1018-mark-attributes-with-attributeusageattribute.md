---
title: CA1018:以 AttributeUsageAttribute 標記屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 404ef250726d12300e2b72150ff42b4f0b7bfb24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662056"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018:必須以 AttributeUsageAttribute 標記屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|分類|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 @No__t_0 屬性不存在於自訂屬性上。

## <a name="rule-description"></a>規則描述
 當您定義自訂屬性時，請使用 <xref:System.AttributeUsageAttribute> 來標示它，以指示原始程式碼中可套用自訂屬性的位置。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 例如，您可以定義一個屬性來識別負責維護和增強程式庫中每個類型的人員，而且該責任一律會在類型層級指派。 在此情況下，編譯器應該啟用類別、列舉和介面上的屬性，但不應在方法、事件或屬性上啟用它。 組織原則和程式會決定是否應該在元件上啟用屬性。

 @No__t_0 列舉會定義您可以為自訂屬性指定的目標。 如果您省略 <xref:System.AttributeUsageAttribute>，則自訂屬性將對所有目標有效，如 <xref:System.AttributeTargets> 列舉的 `All` 值所定義。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用 <xref:System.AttributeUsageAttribute> 來指定屬性的目標。 請參閱下列範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您應該修正此規則的違規，而不是排除訊息。 即使屬性繼承 <xref:System.AttributeUsageAttribute>，該屬性也應該存在，以簡化程式碼維護。

## <a name="example"></a>範例
 下列範例會定義兩個屬性。 `BadCodeMaintainerAttribute` 不正確地省略 <xref:System.AttributeUsageAttribute> 語句，而 `GoodCodeMaintainerAttribute` 會正確地執行本節稍早所述的屬性。 請注意，設計規則 [CA1019 需要屬性 `DeveloperName`：定義屬性引數的存取子 ](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)，並納入以供完整性之用。

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1019：定義屬性引數的存取子 ](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813：避免未密封的屬性 ](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
