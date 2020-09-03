---
title: '>CA1815：覆寫數值型別的 equals 和運算子 equals |Microsoft Docs'
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
ms.openlocfilehash: fc5dc311fd85af2b6a0eb3e29e9932614ca55193
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543906"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815:必須覆寫實值類型上的 Equals 方法和等號比較運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|類別|Microsoft。效能|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用實值型別不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> ，或不會執行相等運算子 (= =) 。 此規則不會檢查列舉。

## <a name="rule-description"></a>規則描述
 如果是實值型別，則繼承的執行會 <xref:System.Object.Equals%2A> 使用反映程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果您希望使用者比較或排序實例，或是使用它們做為雜湊表索引鍵，則您的實值型別應該是實值型別 <xref:System.Object.Equals%2A> 。 如果您的程式設計語言支援運算子多載，則也應該提供相等和不等運算子的實作。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請提供的實作為 <xref:System.Object.Equals%2A> 。 如果可以，請執行等號比較運算子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果實值型別的實例不會彼此比較，就可以安全地隱藏此規則的警告。

## <a name="example-of-a-violation"></a>違規範例

### <a name="description"></a>描述
 下列範例顯示違反此規則的結構 (數值型別) 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>如何修正的範例

### <a name="description"></a>描述
 下列範例會藉由覆寫 <xref:System.ValueType.Equals%2A?displayProperty=fullName> 並執行等號比較運算子來修正先前的違規 (= =、！ =) 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2224:多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226:運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Object.Equals%2A?displayProperty=fullName>
