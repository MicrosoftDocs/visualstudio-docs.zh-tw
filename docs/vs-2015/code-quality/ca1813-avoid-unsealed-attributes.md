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
ms.openlocfilehash: fe5967ef099794b6c71029e9d03d959dd83b01dc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647062"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813：避免使用非密封屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft。效能|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用型別繼承自 <xref:System.Attribute?displayProperty=fullName>，不是抽象的，而且不是密封的（Visual Basic 中 `NotInheritable`）。

## <a name="rule-description"></a>規則描述
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Class Library 會提供擷取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構;例如 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 會搜尋指定的屬性類型，或任何延伸指定之屬性類型的屬性類型。 密封屬性可避免透過繼承階層進行搜尋，並且可以改善效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請密封屬性類型，或將它設為抽象。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 您可以放心地隱藏此規則的警告。 只有當您要定義屬性階層，而且無法密封屬性或使其成為抽象時，才應該執行此動作。

## <a name="example"></a>範例
 下列範例顯示符合此規則的自訂屬性。

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018：必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
