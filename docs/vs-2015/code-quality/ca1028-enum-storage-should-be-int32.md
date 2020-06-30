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
ms.openlocfilehash: 0b2e8ebcc7720f5cd9dc6c700bcc08b68f89e275
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542489"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028:列舉儲存區應該是 Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用列舉的基礎類型不是 <xref:System.Int32?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設， <xref:System.Int32?displayProperty=fullName> 資料類型會用來儲存常數值。 雖然您可以變更此基礎類型，但在大部分的情況下並不需要或不建議這麼做。 請注意，您可以使用小於的資料類型來達到顯著的效能提升 <xref:System.Int32> 。 如果您無法使用預設資料類型，您應該使用其中一個通用語言系統（CLS）相容整數類型、、、 <xref:System.Byte> 或， <xref:System.Int16> <xref:System.Int32> <xref:System.Int64> 以確保列舉的所有值都能以符合 CLS 標準的程式設計語言表示。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，除非存在大小或相容性問題，請使用 <xref:System.Int32> 。 對於 <xref:System.Int32> 不夠大而無法保存值的情況，請使用 <xref:System.Int64> 。 如果回溯相容性需要較小的資料類型，請使用 <xref:System.Byte> 或 <xref:System.Int16> 。

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
 下列範例會將基礎資料類型變更為，藉以修正先前的違規 <xref:System.Int32> 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1008:列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700:不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
