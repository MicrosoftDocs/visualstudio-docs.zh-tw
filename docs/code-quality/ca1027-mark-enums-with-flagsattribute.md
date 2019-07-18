---
title: CA1027:必須以 FlagsAttribute 標記列舉
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdb8406d43f90414cf255abae6f1ca5f549e92e
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842474"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027:必須以 FlagsAttribute 標記列舉

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

列舉之值的乘冪或列舉中所定義的其他值的組合和<xref:System.FlagsAttribute?displayProperty=fullName>屬性不存在。 若要減少誤判，此規則不會報告的違規有連續值的列舉。

根據預設，此規則只會查看公用列舉型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 套用<xref:System.FlagsAttribute>列舉型別時可以有意義地結合其具名的常數。 比方說，請考慮的應用程式，會追蹤哪一天的資源可供使用的一周天數的列舉。 如果要將每個資源的可用性編碼使用列舉型別具有<xref:System.FlagsAttribute>可以表示存在的天數內的任何組合。 如果沒有屬性，可表示一週的某一天。

對於儲存 combinable 列舉的欄位，個別的列舉值會視為欄位中的位元的群組。 因此，這類欄位有時稱為*位元欄位*。 若要結合之列舉值的位元欄位中的儲存體，使用布林值的條件運算子。 若要測試以判斷是否存在特定的列舉值的位元欄位，使用布林值的邏輯運算子。 位元欄位，來儲存和擷取組合的列舉值正確，列舉中定義的每個值必須是 2 的乘冪。 除非這是讓布林值的邏輯運算子不能擷取個別的列舉值，儲存在欄位中。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，加入<xref:System.FlagsAttribute>至列舉。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您不想要組合的列舉值，則隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1027.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

在下列範例中，`DaysEnumNeedsFlags`是一種列舉符合使用需求<xref:System.FlagsAttribute>但沒有它。 `ColorEnumShouldNotHaveFlag`列舉型別沒有 2 乘冪的值，但未正確指定<xref:System.FlagsAttribute>。 這樣會違反規則[CA2217:執行不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)。

[!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>相關的規則

- [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>