---
title: CA1309：使用循序的 StringComparison
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 91953fd855576b6f40d02ebb3653fff07bfdef9c
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546427"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309：使用循序的 StringComparison

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|類別|Microsoft.Globalization|
|中斷變更|非重大|

## <a name="cause"></a>原因

非語言的字串比較作業不會設定<xref:System.StringComparison>參數設為**序數**或是**OrdinalIgnoreCase**。

## <a name="rule-description"></a>規則描述
 許多字串作業，最重要的<xref:System.String.Compare%2A?displayProperty=fullName>並<xref:System.String.Equals%2A?displayProperty=fullName>方法，現在提供的多載，接受<xref:System.StringComparison?displayProperty=fullName>做為參數的列舉值。

 當您指定**StringComparison.Ordinal**或是**StringComparison.OrdinalIgnoreCase**，字串比較為非語言式。 也就是比較批覆後，會忽略自然語言專屬的功能。 忽略自然語言功能表示所做的決策為基礎，以簡單的位元組比較，而不是在大小寫或參數化的文化特性的等價資料表。 如此一來，藉由明確地將參數設定為其中一個**StringComparison.Ordinal**或是**StringComparison.OrdinalIgnoreCase**，程式碼通常可以提升速度、 增加正確性，和會變成更可靠。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將字串比較方法變更為接受的多載<xref:System.StringComparison?displayProperty=fullName>列舉型別做為參數，並指定**序數**或是**OrdinalIgnoreCase**。 例如，將 `String.Compare(str1, str2)` 變更為 `String.Compare(str1, str2, StringComparison.Ordinal)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，或應該使用目前文化特性的語意時的程式庫或應用程式供有限區域的對象。

## <a name="see-also"></a>另請參閱

- [全球化警告](../code-quality/globalization-warnings.md)
- [CA1307：必須指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)