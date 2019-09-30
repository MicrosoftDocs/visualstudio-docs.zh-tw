---
title: CA1008:列舉值中應該要有值為零的成員
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c9b6e48fb82be5a41c420827a32926630bb725ed
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236495"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008:列舉值中應該要有值為零的成員

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|分類|Microsoft.Design|
|重大變更|不中斷-當系統提示您將**None**值新增至非旗標列舉時。 中斷-當系統提示您重新命名或移除任何列舉值時。|

## <a name="cause"></a>原因

未套用的列舉<xref:System.FlagsAttribute?displayProperty=fullName>不會定義值為零的成員。 或者，已<xref:System.FlagsAttribute>套用的列舉會定義值為零的成員，但其名稱不是 ' None '。 或者，列舉會定義多個零值的成員。

根據預設，此規則只會查看外部可見的列舉，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

未初始化列舉的預設值與其他實數值型別一樣，是零。 非旗標屬性列舉應定義值為零的成員，讓預設值是列舉的有效值。 如有需要，請將成員命名為 ' None '。 否則，請將零指派給最常使用的成員。 根據預設，如果宣告中未設定第一個列舉成員的值，其值為零。

如果已套用的<xref:System.FlagsAttribute>列舉定義了零值成員，其名稱應該是 ' None '，表示列舉中未設定任何值。 針對任何其他目的使用零值成員，會與使用<xref:System.FlagsAttribute>相同，因為和和或位運算子對成員毫無用處。 這表示應該只將值零指派給一個成員。 如果有多個值為零的成員出現在旗標屬性列舉中`Enum.ToString()` ，則會針對非零的成員傳回不正確的結果。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正非旗標屬性列舉的此規則違規，請定義值為零的成員。這是不中斷的變更。 針對定義零值成員的旗標屬性列舉，請將此成員命名為 ' None '，並刪除值為零的其他任何成員。這是一種重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

除了先前隨附的旗標屬性列舉以外，請勿隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1008.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示兩個符合規則的列舉，以及違反規則的`BadTraceOptions`列舉。

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>相關規則

- [CA2217不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700不要將列舉值命名為「Reserved」](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712不要使用類型名稱做為列舉值的前置詞](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027 必須使用 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Enum?displayProperty=fullName>