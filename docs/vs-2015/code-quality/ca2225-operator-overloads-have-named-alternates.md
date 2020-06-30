---
title: CA2225：運算子多載具有已命名的替代 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545219"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225:運算子多載必須有具名的替代方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 偵測到運算子多載，且找不到預期的具名替代方法。

## <a name="rule-description"></a>規則描述
 運算子多載允許使用符號來代表類型的計算。 例如，多載加號（+）以進行加法的類型，通常會有一個名為 ' Add ' 的替代成員。 已命名的替代成員可存取與運算子相同的功能，並為以不支援多載運算子的語言設計程式的開發人員提供。

 此規則會檢查下表所列的運算子。

|C#|Visual Basic|C++|替代名稱|
|---------|------------------|-----------|--------------------|
|+ （二進位）|+|+ （二進位）|新增|
|+=|+=|+=|新增|
|&|And|&|BitwiseAnd|
|&=|和 =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|或 =|&#124;=|BitwiseOr|
|--|N/A|--|遞減|
|/|/|/|除以|
|/=|/=|/=|除以|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|Xor =|^=|Xor|
|>|>|>|比較|
|>=|>=|>=|比較|
|++|N/A|++|[遞增]|
|<>|!=|Equals|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|比較|
|<=|<=|\<=|比較|
|&&|N/A|&&|LogicalAnd|
|&#124;&#124;|N/A|&#124;&#124;|LogicalOr|
|!|N/A|!|LogicalNot|
|%|Mod|%|Mod 或餘數|
|%=|N/A|%=|Mod|
|* （二進位）|*|*|乘以|
|*=|N/A|*=|乘以|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|N/A|>>=|RightShift|
|-（二進位）|-（二進位）|-（二進位）|減去|
|-=|N/A|-=|減去|
|true|IsTrue|N/A|IsTrue （屬性）|
| - (一元)   |N/A|-|Negate|
|+ （一元）|N/A|+|加|
|false|IsFalse|False|IsTrue （屬性）|

 N/A = = 無法以選取的語言多載。

 此規則也會藉 `SomeType` 由檢查名為和的方法，檢查類型（）中的隱含和明確轉換運算子 `ToSomeType` `FromSomeType` 。

 在 c # 中，當二元運算子多載時，對應的指派運算子（如果有的話）也會隱含地多載。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請執行運算子的替代方法。使用建議的替代名稱將其命名為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您要執行共用程式庫，請勿隱藏此規則的警告。 應用程式可以忽略此規則的警告。

## <a name="example"></a>範例
 下列範例會定義違反此規則的結構。 若要更正範例，請將公用 `Add(int x, int y)` 方法加入至結構。

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226:運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224:多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
