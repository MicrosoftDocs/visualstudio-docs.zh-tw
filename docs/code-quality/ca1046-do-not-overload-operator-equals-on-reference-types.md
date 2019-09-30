---
title: CA1046:不要多載參考類型上的等號比較運算子
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23358d104c891ff9e230f0daad0f5e6ca57b46c2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235770"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046:不要多載參考類型上的等號比較運算子

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
公用或嵌套的公用參考型別會多載等號比較運算子。

## <a name="rule-description"></a>規則描述
對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請移除等號比較運算子的執行。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
當參考型別的行為類似內建實數值型別時，可以安全地隱藏此規則的警告。 如果對類型的實例執行加法或減法有意義，可能會正確地執行等號比較運算子並抑制違規。

## <a name="example"></a>範例
下列範例示範比較兩個參考時的預設行為。

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>範例

下列應用程式會比較一些參考。

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

這個範例會產生下列輸出：

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>相關規則

[CA1013多載運算子等於 on 多載加和減](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)