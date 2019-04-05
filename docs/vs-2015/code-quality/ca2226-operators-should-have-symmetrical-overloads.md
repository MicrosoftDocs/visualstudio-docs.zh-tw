---
title: CA2226:運算子應該有對稱的多載 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 574f254b1cfccf58def5c404c15b03a4c83658cc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942857"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226:運算子應該有對稱的多載
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 請勿隱藏此規則的警告。 您的型別不適用於與一致的方式[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]。

## <a name="related-rules"></a>相關的規則
 [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225:運算子多載必須有具名的替代項目](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224:覆寫等於多載等號比較運算子](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218:Equals 覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231：在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
