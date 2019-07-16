---
title: CA1027:以 FlagsAttribute 標記列舉 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6603e0869a9eb7947735c52a4c438b39d64b9140
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157717"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027:必須以 FlagsAttribute 標記列舉
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用列舉之值的乘冪或列舉中所定義的其他值的組合和<xref:System.FlagsAttribute?displayProperty=fullName>屬性不存在。 若要減少誤判，此規則不會報告的違規有連續值的列舉。

## <a name="rule-description"></a>規則描述
 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 套用<xref:System.FlagsAttribute>列舉型別時可以有意義地結合其具名的常數。 比方說，請考慮的應用程式，會追蹤哪一天的資源可供使用的一周天數的列舉。 如果要將每個資源的可用性編碼使用列舉型別具有<xref:System.FlagsAttribute>可以表示存在的天數內的任何組合。 如果沒有屬性，可表示一週的某一天。

 對於儲存 combinable 列舉的欄位，個別的列舉值會視為欄位中的位元的群組。 因此，這類欄位有時稱為*位元欄位*。 若要結合之列舉值的位元欄位中的儲存體，使用布林值的條件運算子。 若要測試以判斷是否存在特定的列舉值的位元欄位，使用布林值的邏輯運算子。 位元欄位，來儲存和擷取組合的列舉值正確，列舉中定義的每個值必須是 2 的乘冪。 除非這是讓布林值的邏輯運算子不能擷取個別的列舉值，儲存在欄位中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入<xref:System.FlagsAttribute>至列舉。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不想要組合的列舉值，則隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，`DaysEnumNeedsFlags`是一種列舉符合使用需求<xref:System.FlagsAttribute>，但不要讓它。 `ColorEnumShouldNotHaveFlag`列舉型別沒有值的乘冪數，但未正確指定<xref:System.FlagsAttribute>。 這樣會違反規則[CA2217:執行不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)。

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱
 <xref:System.FlagsAttribute?displayProperty=fullName>
