---
title: CA1815：覆寫實數值型別的 equals 和 operator equals |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bb9574eb6e9f907d4b1fcc74f50fca0e7db85253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668398"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815：覆寫實值類型上的等號和等號比較運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Category|Microsoft。效能|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用實值型別不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName>，或不會執行等號比較運算子（= =）。 此規則不會檢查列舉。

## <a name="rule-description"></a>規則描述
 對於實值型別，<xref:System.Object.Equals%2A> 的繼承執行會使用反映程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果您想要讓使用者比較或排序實例，或是將它們當做雜湊表索引鍵使用，則您的實值型別應該會執行 <xref:System.Object.Equals%2A>。 如果您的程式設計語言支援運算子多載，則也應該提供相等和不等運算子的實作。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請提供 <xref:System.Object.Equals%2A> 的執行。 如果可以，請執行等號比較運算子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果不會比較數值型別的實例，則可以放心地隱藏此規則的警告。

## <a name="example-of-a-violation"></a>違規的範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的結構（實值型別）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>如何修正的範例

### <a name="description"></a>描述
 下列範例會覆寫 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 並執行等號比較運算子（= =、！ =），藉以修正先前的違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>請參閱
 <xref:System.Object.Equals%2A?displayProperty=fullName>
