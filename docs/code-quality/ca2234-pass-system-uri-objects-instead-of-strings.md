---
title: CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07e0bbaa05b0674666a7d4403daeeee8b23348be
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919973"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串
|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 呼叫的方法有字串參數名稱包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url";和方法的宣告型別包含對應的方法多載具有<xref:System.Uri?displayProperty=fullName>參數。

## <a name="rule-description"></a>規則描述
 參數名稱會分成 camel 命名法的大小寫慣例為基礎的權杖，然後每個語彙基元會檢查以查看它是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，此參數會假設代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別以安全的方式提供這些服務。 當只有有關 URI 表示方式的兩個多載之間有選擇時，使用者應該選擇的多載，<xref:System.Uri>引數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫的多載，<xref:System.Uri>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果字串參數不代表 URI。

## <a name="example"></a>範例
 下列範例會示範一種方法， `ErrorProne`，這違反規則和方法， `SaferWay`，正確地呼叫<xref:System.Uri>多載。

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)