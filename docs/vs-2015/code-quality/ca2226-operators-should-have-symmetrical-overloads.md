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
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540565"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226:運算子應該有對稱的多載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。

## <a name="rule-description"></a>規則描述
 在沒有任何情況下，相等或不等比較適用于型別的實例，而相反的運算子未定義。 型別通常會藉由傳回相等運算子的否定值來執行不等比較運算子。

 C # 編譯器會發出此規則違規的錯誤。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請同時執行相等和不等比較運算子，或移除存在的相等運算子。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 您的類型將無法以與一致的方式運作 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="related-rules"></a>相關規則
 [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225:運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224:多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
