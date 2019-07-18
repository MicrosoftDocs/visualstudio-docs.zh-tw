---
title: CA2231:在覆寫 ValueType.Equals 上多載等號運算子
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ec5f3bd1dfe66451ceff0b3af334a75aafb2e0b1
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841628"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231:在覆寫 ValueType.Equals 上多載等號運算子

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

實值型別會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>但不會實作等號比較運算子。

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

在大部分的程式設計語言，不會有預設實作實值型別中使用等號比較運算子 （= =）。 如果您的程式語言支援運算子多載，您應該考慮實作等號比較運算子。 其行為應該與相同<xref:System.Object.Equals%2A>。

您無法使用預設等號比較運算子多載等號比較運算子的實作中。 這樣會導致堆疊溢位。 若要實作等號比較運算子，請在您的實作中使用 Object.Equals 方法。 例如：

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，實作等號比較運算子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

安全地隱藏的警告，這項規則;不過，我們建議您盡可能提供等號比較運算子。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca2231.api_surface = private, internal
```

您可以設定此選項只是這項規則，所有規則，或所有規則 （使用） 這個類別中。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例會定義違反此規則的型別：

[!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2225:運算子多載必須有具名的替代項目](../code-quality/ca2225-operator-overloads-have-named-alternates.md)
- [CA2226:運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224:覆寫等於多載等號比較運算子](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218:Equals 覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Object.Equals%2A?displayProperty=fullName>