---
title: CA1309：使用循序的 StringComparison
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 964dfee8b8ed78de76ead4ee5eda63fe0a49a72c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309：使用循序的 StringComparison
|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|分類|Microsoft.Globalization|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非語言的字串比較作業不會設定<xref:System.StringComparison>參數設為 **序數**或**OrdinalIgnoreCase**。

## <a name="rule-description"></a>規則描述
 許多字串作業，最重要<xref:System.String.Compare%2A?displayProperty=fullName>和<xref:System.String.Equals%2A?displayProperty=fullName>方法，現在會提供可接受的多載<xref:System.StringComparison?displayProperty=fullName>做為參數的列舉值。

 當您指定**StringComparison.Ordinal**或**StringComparison.OrdinalIgnoreCase**，將非語言的字串比較。 也就是比較決定時，會忽略自然語言特有的功能。 這表示的決策根據簡單全半形比較，忽略大小寫或對等會由文化特性參數化的資料表。 如此一來，由明確地將參數設為  **StringComparison.Ordinal**或**StringComparison.OrdinalIgnoreCase**，您的程式碼通常可以提升速度、 增加正確性，而且會變成更可靠。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將字串比較方法變更為可接受的多載<xref:System.StringComparison?displayProperty=fullName>列舉型別做為參數，並指定**序數**或**OrdinalIgnoreCase**。 例如，變更`String.Compare(str1, str2)`至`String.Compare(str1, str2, StringComparison.Ordinal)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，當程式庫或應用程式適用於有限制的本機使用者，或應該使用目前文化特性的語意。

## <a name="see-also"></a>另請參閱
 [全球化警告](../code-quality/globalization-warnings.md) [CA1307： 指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)