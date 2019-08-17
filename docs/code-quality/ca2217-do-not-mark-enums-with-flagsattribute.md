---
title: CA2217:不要以 FlagsAttribute 標記列舉
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 377188183acdaa9aa86ae3344c8f6d5727b82ccc
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69546845"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:不要以 FlagsAttribute 標記列舉

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Category|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

列舉標記<xref:System.FlagsAttribute>為, 而且有一或多個值不是兩個的乘冪, 或在列舉上有其他已定義值的組合。

根據預設, 此規則只會查看外部可見的列舉, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

只有在列舉中<xref:System.FlagsAttribute>所定義的每個值是二的乘冪或已定義值的組合時, 列舉才會出現。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請<xref:System.FlagsAttribute>從列舉中移除。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca2217.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (使用方式) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="examples"></a>範例

下列程式碼顯示列舉, `Color`其中包含值3。 3不是兩個的乘冪, 或任何已定義值的組合。 列舉不應<xref:System.FlagsAttribute>標記為。 `Color`

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

下列程式碼顯示的列舉, `Days`符合以<xref:System.FlagsAttribute>標記的需求:

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>相關規則

[CA1027 必須使用 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>
