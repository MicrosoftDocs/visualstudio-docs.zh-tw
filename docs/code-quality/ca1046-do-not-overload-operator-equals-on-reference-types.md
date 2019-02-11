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
ms.openlocfilehash: 9f9304fcd86a9b36a729b1436fe16471b449ac0d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953759"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046:不要多載參考類型上的等號比較運算子

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或巢狀公用參考型別多載等號比較運算子。

## <a name="rule-description"></a>規則描述
 對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除位在相等運算子的實作。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，當參考類型的行為類似內建實值型別。 如果是類型的進行加法或減法運算執行個體上的有意義的則可能是類型的正確實作等號比較運算子，並隱藏此違規情形。

## <a name="example"></a>範例
 比較兩個參考時，下列範例會示範預設行為。

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>範例

下列應用程式會比較某些參考。

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

這個範例會產生下列輸出：

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>相關的規則

[CA1013:多載運算子等於多載加號和減號](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)