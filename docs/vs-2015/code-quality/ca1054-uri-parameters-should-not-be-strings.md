---
title: CA1054:URI 參數不應為字串 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2062c7518545300074a0377b7a9cca7ddf1a8aa5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603373"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054:URI 參數不應該為字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|分類|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型宣告了一個方法，其字串參數的名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"，而類型未宣告採用 <xref:System.Uri?displayProperty=fullName> 參數的對應多載。

## <a name="rule-description"></a>規則描述
 此規則會根據 camel 大小寫慣例，將參數名稱分割成權杖，並檢查每個權杖是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果相符，此規則會假設參數代表統一資源識別元（URI）。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 如果方法接受 URI 的字串標記法，則應提供對應的多載，以取得 <xref:System.Uri> 類別的實例，這會以安全且安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將參數變更為 <xref:System.Uri> 類型;這是一種重大變更。 或者，提供採用 <xref:System.Uri> 參數之方法的多載;這是不間斷的變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果參數不代表 URI，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型 `ErrorProne`，以及符合規則的類型 `SaferWay`。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1056：URI 屬性不應該是字串 ](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055：URI 傳回值不應為字串 ](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234：傳遞 System.object 物件，而不是字串 ](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057：字串 URI 多載會呼叫 System.object 多載 ](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
