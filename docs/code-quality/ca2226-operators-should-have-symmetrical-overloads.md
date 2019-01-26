---
title: CA2226:運算子應該有對稱的多載
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6a38f6f4e76f5195e042b0ede2b2a8a5384a1cf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938012"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226:運算子應該有對稱的多載

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。

## <a name="rule-description"></a>規則描述
 沒有其中相等或不等比較是適用於類型的執行個體，而相反的運算子是未定義的情況。 通常，型別會實作不等比較運算子所傳回的等號比較運算子的相反的值。

 C# 編譯器會發出這項規則的違規錯誤。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作相等和不等比較運算子，或移除的存在。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 您的型別與.NET Framework 一致的方式，將無法運作。

## <a name="related-rules"></a>相關的規則
 [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225:運算子多載必須有具名的替代項目](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224:覆寫等於多載等號比較運算子](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218:Equals 覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)