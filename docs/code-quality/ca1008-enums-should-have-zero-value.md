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
ms.openlocfilehash: 4bb79d2944bdb49c59fd53fb30e1497c57c5c516
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868281"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008:列舉值中應該要有值為零的成員

|||
|-|-|
|TypeName|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|分類|Microsoft.Design|
|中斷變更|非中斷-當系統提示您新增**無**非旗標列舉的值。 -系統會提示您重新命名或移除任何列舉值時中斷。|

## <a name="cause"></a>原因

列舉型別沒有套用<xref:System.FlagsAttribute?displayProperty=fullName>不會定義具有零值的成員。 或列舉型別具有套用<xref:System.FlagsAttribute>定義的成員，其值為零，但其名稱不是 'None'。 或者，您也可以列舉會定義多個值為零的成員。

根據預設，此規則只會查看外部可見的列舉型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

未初始化的列舉型別，如同其他實值型別，預設值為零。 非旗標屬性的列舉型別應該定義的值為零，以便預設值是有效的值，列舉型別的成員。 如果適當的話，命名為成員 'None'。 否則，指定零給最常使用的成員。 根據預設，如果第一個列舉成員的值未在宣告中，設定其值會是零。

如果列舉型別具有<xref:System.FlagsAttribute>套用定義零值的成員，其名稱應該是 'None' 表示列舉型別中，已設定任何值。 使用值為零的成員，與使用任何其他用途為<xref:System.FlagsAttribute>，AND 和或位元運算子會與成員變成毫無用處。 這表示該只有一個成員應該指派值為零。 如果值為零的多個成員會發生在旗標屬性的列舉，`Enum.ToString()`不是零的成員會傳回不正確的結果。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正非屬性旗標列舉型別為此規則的違規情形，定義成員，其值為零，這是不間斷的變更。 旗標屬性的列舉定義零值的成員，命名這個成員為 'None'，並刪除任何其他的值為零; 的成員這是一項重大變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏除了先前所提供的旗標屬性列舉此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1008.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示兩個符合規則的列舉和列舉型別， `BadTraceOptions`，會違反此規則。

[!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
[!code-csharp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
[!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]

## <a name="related-rules"></a>相關的規則

- [CA2217:不以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)
- [CA1700:未命名的列舉值 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)
- [CA1712:不要使用型別名稱的列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)
- [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)
- [CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Enum?displayProperty=fullName>