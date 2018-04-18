---
title: CA1046： 請勿多載參考類型上的等號比較運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e78217e2ce8613ca312a96058b4477d1da82a5e7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046：請勿多載參考類型上的等號比較運算子
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
 若要修正此規則的違規情形，請移除等號比較運算子的實作。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，當參考類型的行為類似的內建實值類型。 如果是類型的有意義的加法或減法運算執行個體上的執行，則可能是類型的正確實作等號比較運算子和隱藏違規。  
  
## <a name="example"></a>範例  
 比較兩個參考時，下列範例會示範預設行為。  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>範例  
 下列應用程式比較部分的參考。  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 此範例會產生下列輸出。  
  
 **= 新 (2，2) 且 b = 相等的新 (2，2)？沒有**  
**c 和相等嗎？[是]**  
**b 和 a = = 嗎？沒有**  
**c 和 a = = 嗎？[是]**   
## <a name="related-rules"></a>相關的規則  
 [CA1013：多載加號和減號運算子時必須一併多載等號比較運算子](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [等號比較運算子](/dotnet/standard/design-guidelines/equality-operators)