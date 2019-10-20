---
title: CA2226：運算子應該有對稱的多載 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9772577c2b1466cf3d1b5267129aa761db983021
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658898"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226：運算子應該有對稱的多載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。

## <a name="rule-description"></a>規則描述
 在某些情況下，不相等或不等比較適用于類型的實例，而且相反的運算子未定義。 類型通常會藉由傳回等號比較運算子的負值來實作為不等運算子。

 C#編譯器會發出錯誤，以違反此規則。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請同時執行相等和不等比較運算子，或移除其中一項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 您的類型將無法以與 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 一致的方式來使用。

## <a name="related-rules"></a>相關規則
 [CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225：運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
