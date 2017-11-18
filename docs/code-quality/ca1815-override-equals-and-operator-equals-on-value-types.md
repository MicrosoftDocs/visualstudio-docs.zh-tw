---
title: "Ca1815： 覆和實值類型上等號比較運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20b31e4ea20fd3d1a4ec254507962bf4e8946bb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815：覆寫實值類型上的等號和等號比較運算子
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|分類|Microsoft.Performance|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 公用實值類型不會覆寫<xref:System.Object.Equals%2A?displayProperty=fullName>，或未實作等號比較運算子 （= =）。 此規則不會檢查列舉型別。  
  
## <a name="rule-description"></a>規則描述  
 針對實值類型的繼承實作<xref:System.Object.Equals%2A>會使用 Reflection 程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果您預期使用者比較或排序執行個體，或使用它們做為雜湊資料表索引鍵，值類型應實作<xref:System.Object.Equals%2A>。 如果您的程式語言支援運算子多載，也應該提供相等和不等比較運算子的實作。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，提供的實作<xref:System.Object.Equals%2A>。 如果可以，您可以實作等號比較運算子。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果實值類型的執行個體不會相互比較。  
  
## <a name="example-of-a-violation"></a>發生違規的範例  
  
### <a name="description"></a>描述  
 下列範例顯示違反此規則的結構 （實值型別）。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>範例，示範如何修正  
  
### <a name="description"></a>描述  
 下列範例會藉由覆寫修正上述違規<xref:System.ValueType.Equals%2A?displayProperty=fullName>和實作等號比較運算子 (= =、 ！ =)。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Object.Equals%2A?displayProperty=fullName>