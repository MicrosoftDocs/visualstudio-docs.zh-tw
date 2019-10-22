---
title: CA1028：列舉儲存區應該是 Int32 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc1039cb547a48c4f2dd3ea869b46d4706e9c3a2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661909"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028：列舉儲存區應該是 Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 不 <xref:System.Int32?displayProperty=fullName> 公用列舉的基礎類型。

## <a name="rule-description"></a>規則描述
 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，<xref:System.Int32?displayProperty=fullName> 資料類型會用來儲存常數值。 雖然您可以變更此基礎類型，但在大部分的情況下並不需要或不建議這麼做。 請注意，使用的資料類型若小於 <xref:System.Int32>，就無法達到顯著的效能提升。 如果您無法使用預設資料類型，您應該使用其中一個通用語言系統（CLS）相容整數類型，<xref:System.Byte>，<xref:System.Int16>，<xref:System.Int32> 或 <xref:System.Int64>，以確保列舉的所有值都可以在符合 CLS 標準的程式設計中表示語言。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，除非有大小或相容性問題，否則請使用 <xref:System.Int32>。 在 <xref:System.Int32> 不夠大而無法容納值的情況下，請使用 <xref:System.Int64>。 如果回溯相容性需要較小的資料類型，請使用 <xref:System.Byte> 或 <xref:System.Int16>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有在回溯相容性問題需要時，才隱藏此規則的警告。 在應用程式中，如果無法符合此規則，通常不會造成問題。 在需要語言互通性的程式庫中，如果不符合此規則，可能會對使用者造成不良影響。

## <a name="example-of-a-violation"></a>違規的範例

### <a name="description"></a>描述
 下列範例顯示兩個不使用建議之基礎資料類型的列舉。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>如何修正的範例

### <a name="description"></a>描述
 下列範例會將基礎資料類型變更為 <xref:System.Int32>，藉以修正先前的違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700：不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>請參閱
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
