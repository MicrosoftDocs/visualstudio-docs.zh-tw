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
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778992"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036:必須在 Comparable 類型中覆寫方法

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

類型會實作<xref:System.IComparable?displayProperty=fullName>介面，並不會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>或沒有多載等號比較，是否不相等，語言特定比較運算子比較不-，或大於-比。 如果型別繼承介面的實作，此規則就不會報告違規情形。

根據預設，此規則只會查看公用和受保護的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

定義自訂的排序順序的型別會實作<xref:System.IComparable>介面。 <xref:System.IComparable.CompareTo%2A>方法會傳回整數值，指出兩個型別執行個體的正確的排序次序。 此規則會識別設定的排序順序的類型。 設定排序順序表示的相等的一般意義，不相等，-和更新版本-不套用。 當您提供的實作<xref:System.IComparable>，您通常必須也會覆寫<xref:System.Object.Equals%2A>使其傳回值，都必須配合<xref:System.IComparable.CompareTo%2A>。 如果您覆寫<xref:System.Object.Equals%2A>撰寫的程式碼和語言支援運算子多載，您也應該提供一致的運算子<xref:System.Object.Equals%2A>。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，覆寫<xref:System.Object.Equals%2A>。 如果您的程式語言支援運算子多載，提供下列運算子：

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

在 C# 中，用來表示這些運算子的語彙基元如下所示：

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏規則 ca1036 必須時違規因遺漏運算子和您的程式語言不支援運算子多載，在此情況下，使用 Visual Basic 的警告。 如果您判斷，實作運算子不合理在您的應用程式內容中，也很安全地隱藏此規則的警告時它就會引發 op_Equality 以外的等號比較運算子。 不過，您應該一律覆寫 op_Equality 與 = = 運算子，如果您覆寫<xref:System.Object.Equals%2A?displayProperty=nameWithType>。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="examples"></a>範例

下列程式碼包含的類型，會正確地實作<xref:System.IComparable>。 程式碼註解指出方法以滿足相關的各種規則<xref:System.Object.Equals%2A>而<xref:System.IComparable>介面。

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

下列應用程式程式碼測試的行為<xref:System.IComparable>稍早所示的實作。

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)