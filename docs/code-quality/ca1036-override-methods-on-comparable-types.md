---
title: CA1036:必須在 Comparable 類型中覆寫方法
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a4e04e1afdbecdc9c333ea43a52bff3123d448a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547615"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036:必須在 Comparable 類型中覆寫方法

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft.Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因

型<xref:System.IComparable?displayProperty=fullName>別會實作用介面, 而且不<xref:System.Object.Equals%2A?displayProperty=fullName>會覆寫或不會針對相等、不等、小於或大於, 將語言特定的運算子多載。 如果類型只繼承介面的執行, 此規則就不會報告違規。

根據預設, 此規則只會查看公用和受保護的類型, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

定義自訂排序次序的類型會執行<xref:System.IComparable>介面。 <xref:System.IComparable.CompareTo%2A>方法會傳回整數值, 表示類型的兩個實例的正確排序次序。 此規則會識別設定排序次序的類型。 設定排序次序表示相等、不等、小於和大於的一般意義不適用。 當您提供的<xref:System.IComparable>執行時, 通常也必須覆寫<xref:System.Object.Equals%2A> , 使其傳回與<xref:System.IComparable.CompareTo%2A>一致的值。 如果您覆<xref:System.Object.Equals%2A>寫並以支援運算子多載的語言撰寫程式碼, 您也應該提供與<xref:System.Object.Equals%2A>一致的運算子。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請<xref:System.Object.Equals%2A>覆寫。 如果您的程式設計語言支援運算子多載, 請提供下列運算子:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

在C#中, 用來表示這些運算子的標記如下:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

當違規是由遺漏運算子所造成, 而您的程式語言不支援運算子多載時, 可以安全地隱藏來自規則 CA1036 必須的警告, 如同 Visual Basic 的情況。 如果您決定在應用程式內容中執行運算子並不合理, 則在 op_Equality 以外的等號比較運算子上引發警告時, 也可以安全地隱藏此規則的警告。 不過, 如果您覆寫<xref:System.Object.Equals%2A?displayProperty=nameWithType>, 您應該一律覆寫 op_Equality 和 = = 運算子。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (設計) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="examples"></a>範例

下列程式碼包含正確實行<xref:System.IComparable>的類型。 程式碼批註會識別符合與<xref:System.Object.Equals%2A> <xref:System.IComparable>和介面相關之各種規則的方法。

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

下列應用程式代碼會測試稍早所<xref:System.IComparable>示之執行的行為。

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)