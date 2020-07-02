---
title: CA1056： URI 屬性不應該是字串 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87ed8f7a291c95e500196f511c6fec0f38cef68e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539408"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056:URI 屬性不應該為字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型會宣告字串屬性，其名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。

## <a name="rule-description"></a>規則描述
 此規則會根據 Pascal 大小寫慣例，將屬性名稱分割成權杖，並檢查每個權杖是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果相符，此規則會假設屬性代表統一資源識別元（URI）。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri?displayProperty=fullName>類別以安全且安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性變更為 <xref:System.Uri> 類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果屬性不代表 URI，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示 `ErrorProne` 違反此規則的類型，以及 `SaferWay` 符合規則的類型。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234:必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
