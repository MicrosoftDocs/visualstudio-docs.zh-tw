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
ms.openlocfilehash: 94666390cc49f365b9f036b076bcd97d68d4edb9
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872284"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217:不要以 FlagsAttribute 標記列舉

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

列舉型別會標示<xref:System.FlagsAttribute>和它有一個或多個值不是兩種或多種其他的次方列舉型別上定義的值。

根據預設，此規則只會查看外部可見的列舉型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

列舉型別應該有<xref:System.FlagsAttribute>目前只有在列舉中定義的每個值是兩個或組合的乘冪定義值。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請移除<xref:System.FlagsAttribute>列舉中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca2217.api_surface = private, internal
```

您可以設定此選項只是這項規則，所有規則，或所有規則 （使用） 這個類別中。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="examples"></a>範例

下列程式碼顯示列舉型別， `Color`，其中包含的值是 3。 3 不是兩個或任何已定義的值組合的乘冪。 `Color`列舉型別不應該以標示<xref:System.FlagsAttribute>。

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

下列程式碼顯示列舉`Days`，符合的需求標示<xref:System.FlagsAttribute>:

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>相關的規則

[CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.FlagsAttribute?displayProperty=fullName>
