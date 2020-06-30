---
title: CA1027 必須：使用 FlagsAttribute 標記列舉 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 774279dd05bd14c34df7f1d450f00599812d6a5b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544504"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027:必須以 FlagsAttribute 標記列舉
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|類別|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用列舉的值為二的冪，或為列舉中所定義之其他值的組合，且 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性不存在。 為了減少誤報，此規則不會針對具有連續值的列舉報告違規。

## <a name="rule-description"></a>規則描述
 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 <xref:System.FlagsAttribute>當可以有意義地結合其命名常數時，將套用至列舉。 例如，請考慮一個在應用程式中持續追蹤哪一天的資源可供使用的列舉。 如果每個資源的可用性是使用已存在的列舉來編碼 <xref:System.FlagsAttribute> ，則可以表示任何天數的組合。 如果沒有屬性，則只能表示一周中的一天。

 對於儲存可組合列舉的欄位，會將個別的列舉值視為欄位中的位群組。 因此，這類欄位有時稱為「*位欄位*」。 若要在位欄位中結合儲存體的列舉值，請使用布林條件運算子。 若要測試位欄位以判斷是否有特定的列舉值，請使用布林邏輯運算子。 為了讓位欄位正確地儲存和取得結合的列舉值，列舉中所定義的每個值都必須是二的乘冪。 除非這麼做，否則布林邏輯運算子將無法解壓縮儲存在欄位中的個別列舉值。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將新增 <xref:System.FlagsAttribute> 至列舉。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不想要組合列舉值，請隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中， `DaysEnumNeedsFlags` 是符合使用之需求的列舉型別 <xref:System.FlagsAttribute> ，但沒有它。 `ColorEnumShouldNotHaveFlag`列舉的值不是2的乘冪，但不正確地指定 <xref:System.FlagsAttribute> 。 這會違反規則[CA2217：請勿使用 FlagsAttribute 標記](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)列舉。

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>
