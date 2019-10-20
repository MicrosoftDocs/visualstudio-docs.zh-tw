---
title: CA1309：使用序數 StringComparison |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOrdinalStringComparison
- CA1309
helpviewer_keywords:
- UseOrdinalStringComparison
- CA1309
ms.assetid: 19be0854-cb6e-4efd-a4c8-a5c1fc6f7a71
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34054f6f444e503077c1e81da9f08ae2832d635a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661424"
---
# <a name="ca1309-use-ordinal-stringcomparison"></a>CA1309：使用循序的 StringComparison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseOrdinalStringComparison|
|CheckId|CA1309|
|Category|Microsoft。全球化|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 Nonlinguistic 的字串比較作業並不會將 <xref:System.StringComparison> 參數設定為**序數**或**OrdinalIgnoreCase**。

## <a name="rule-description"></a>規則描述
 許多字串作業（最重要的 <xref:System.String.Compare%2A?displayProperty=fullName> 和 <xref:System.String.Equals%2A?displayProperty=fullName> 方法）現在提供了一個可接受 <xref:System.StringComparison?displayProperty=fullName> 列舉值做為參數的多載。

 當您指定**StringComparison**或**StringComparison**時，字串比較將會是 nonlinguistic。 也就是說，在進行比較決策時，會忽略自然語言特有的功能。 這表示決策是以簡單的位元組比較為基礎，並略過文化特性所參數化的大小寫或等價資料表。 因此，藉由明確地將參數設定為**StringComparison**或**StringComparison**，您的程式碼通常會獲得速度、提高正確性，而且變得更可靠。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將字串比較方法變更為可接受 <xref:System.StringComparison?displayProperty=fullName> 列舉做為參數的多載，並指定**序數**或**OrdinalIgnoreCase**。 例如，將 `String.Compare(str1, str2)` 變更為 `String.Compare(str1, str2, StringComparison.Ordinal)`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當程式庫或應用程式適用于有限的本機物件，或應該使用目前文化特性的語義時，可以安全地隱藏此規則的警告。

## <a name="see-also"></a>請參閱
 [全球化警告](../code-quality/globalization-warnings.md) [CA1307：指定 StringComparison](../code-quality/ca1307-specify-stringcomparison.md)
