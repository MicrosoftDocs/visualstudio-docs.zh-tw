---
title: CA2225:運算子多載必須有具名的替代方法
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c027bc4581919f814b4d93eacba77248349fdf8b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231080"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225:運算子多載必須有具名的替代方法

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

偵測到運算子多載，但找不到預期的名稱替代方法。

根據預設，此規則只會查看外部可見的類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

運算子多載允許使用符號來代表類型的計算。 例如，多載加號（+）以進行加法的類型，通常會有一個名為 ' Add ' 的替代成員。 已命名的替代成員可存取與運算子相同的功能，並為以不支援多載運算子的語言設計程式的開發人員提供。

此規則會檢查下表所列的運算子。

|C#|Visual Basic|C++|替代名稱|
|---------|------------------|-----------|--------------------|
|+ （二進位）|+|+ （二進位）|新增|
|+=|+=|+=|新增|
|&|和|&|BitwiseAnd|
|&=|和 =|&=|BitwiseAnd|
|&#124;|或|&#124;|BitwiseOr|
|&#124;=|或 =|&#124;=|BitwiseOr|
|--|N/A|--|遞減|
|/|/|/|分割|
|/=|/=|/=|分割|
|==|=|==|等於|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|比較|
|>=|>=|>=|比較|
|++|N/A|++|遞增|
|<>|!=|等於|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|比較|
|<=|<=|\<=|比較|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|
|!|N/A|!|LogicalNot|
|%|Mod|%|Mod 或餘數|
|%=|N/A|%=|Mod|
|* （二進位）|*|*|乘法|
|*=|N/A|*=|乘法|
|~|否|~|OnesComplement|
|>>|>>|>>|RightShift|
=|N/A|>>=|RightShift|
|-（二進位）|-（二進位）|-（二進位）|差集|
|-=|N/A|-=|差集|
|true|IsTrue|N/A|IsTrue （屬性）|
|-（一元）|N/A|-|反|
|+ （一元）|N/A|+|增加|
|False|IsFalse|False|IsTrue （屬性）|

N/A = = 無法以選取的語言多載。

此規則也會藉由檢查名`SomeType` `ToSomeType`為和`FromSomeType`的方法，檢查類型（）中的隱含和明確轉換運算子。

在C#中，當二元運算子多載時，對應的指派運算子（如果有的話）也會隱含地多載。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請執行運算子的替代方法。使用建議的替代名稱將其命名為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您要執行共用程式庫，請勿隱藏此規則的警告。 應用程式可以忽略此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（使用方式）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例會定義違反此規則的結構。 若要更正範例，請將公用`Add(int x, int y)`方法加入至結構。

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>相關規則

- [CA1046不要多載參考型別上的運算子 equals](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224多載運算子 equals 的覆寫 equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218覆寫覆寫 Equals 上的 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)