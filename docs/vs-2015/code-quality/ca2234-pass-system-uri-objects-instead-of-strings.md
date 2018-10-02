---
title: Ca2234： 必須傳遞 System.Uri 物件而非字串 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cba04480cafc5aaed0ee31523d1a5f159cb6fe26
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588482"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[ca2234 必須： 傳遞 System.Uri 物件而非字串](https://docs.microsoft.com/visualstudio/code-quality/ca2234-pass-system-uri-objects-instead-of-strings)。

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 具有字串參數，其名稱中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"; 方法呼叫和方法的宣告型別包含對應的方法多載具有<xref:System.Uri?displayProperty=fullName>參數。

## <a name="rule-description"></a>規則描述
 參數名稱會分割成駝峰式命名法大小寫慣例為基礎的權杖，然後每個語彙基元會檢查以查看它是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，則參數會假設代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別會提供這些服務安全的方式。 使用者之間的差異只關於 URI 的表示法的兩個多載有所選擇，應該選擇採用的多載<xref:System.Uri>引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請呼叫採用的多載<xref:System.Uri>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果字串參數不代表 URI。

## <a name="example"></a>範例
 下列範例示範的方法中， `ErrorProne`，這會違反此規則和方法， `SaferWay`，正確地呼叫<xref:System.Uri>多載。

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)



