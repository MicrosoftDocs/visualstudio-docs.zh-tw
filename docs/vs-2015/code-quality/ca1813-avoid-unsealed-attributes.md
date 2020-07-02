---
title: CA1813：避免未密封的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543945"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813:避免使用非密封屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|類別|Microsoft。效能|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別繼承自 <xref:System.Attribute?displayProperty=fullName> 、不是抽象的，而且不是密封的（ `NotInheritable` 在 Visual Basic 中）。

## <a name="rule-description"></a>規則描述
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Class Library 會提供擷取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構;例如 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> ，搜尋指定的屬性型別，或任何擴充指定屬性型別的屬性型別。 密封屬性可避免透過繼承階層進行搜尋，並且可以改善效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請密封屬性類型，或將它設為抽象。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。 只有當您要定義屬性階層，而且無法密封屬性或使其成為抽象時，才應該執行此動作。

## <a name="example"></a>範例
 下列範例顯示符合此規則的自訂屬性。

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1019:定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018:必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
