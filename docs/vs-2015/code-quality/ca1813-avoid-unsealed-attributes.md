---
title: CA1813： 避免使用非密封的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 97eeacdb0753b0e1b3c42ba83245ba6ace9734d7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830544"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813：避免使用非密封屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|分類|Microsoft.Performance|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型繼承自<xref:System.Attribute?displayProperty=fullName>、 不是抽象的而且不密封 (`NotInheritable` Visual Basic 中)。

## <a name="rule-description"></a>規則描述
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Class Library 會提供擷取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構中;例如<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>搜尋指定的屬性類型或任何延伸指定的屬性類型的屬性類型。 密封屬性排除整個繼承階層架構中，搜尋，並可改善效能。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請密封屬性類型，或將它設為抽象。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告。 如果您正在定義的屬性階層和無法密封屬性或不將它設為抽象，您應該這麼做。

## <a name="example"></a>範例
 下列範例顯示自訂屬性，以符合這項規則。

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018：必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>另請參閱
 [屬性](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



