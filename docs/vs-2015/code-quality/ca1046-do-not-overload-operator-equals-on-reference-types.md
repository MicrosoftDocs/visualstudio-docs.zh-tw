---
title: CA1046：不多載參考型別上的 operator equals |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 118c29473db09d5ed0a4fa447e27e593a88f98b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546753"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046:不要多載參考類型上的等號比較運算子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 Public 或 nested public 參考型別多載等號比較運算子。

## <a name="rule-description"></a>規則描述
 對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除相等運算子的實作為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當參考型別的行為類似內建實值型別時，可以安全地隱藏此規則的警告。 如果在類型的實例上進行加法或減法有意義，則可能會正確地執行等號比較運算子並隱藏違規。

## <a name="example"></a>範例
 下列範例示範比較兩個參考時的預設行為。

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>範例
 下列應用程式會比較某些參考。

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 此範例會產生下列輸出。

 **a = new (2，2) 和 b = new (2，2) 相等嗎？沒有** 
 **c 和 a 相等嗎？是** 
 **b，a 是 = =？沒有** 
 **c 和 a = =？是**
## <a name="related-rules"></a>相關規則
 [CA1013:多載加號和減號運算子時必須一併多載等號比較運算子](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Object.Equals%2A?displayProperty=fullName>[等號比較運算子](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
