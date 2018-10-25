---
title: 'CA1056: URI 屬性不應該為字串 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
helpviewer_keywords:
- UriPropertiesShouldNotBeStrings
- CA1056
ms.assetid: fdc99d29-0904-4a65-baa8-4f76833c953e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1f5ac2b8df8712f4443f2f25ff9270d65cb13bac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884247"
---
# <a name="ca1056-uri-properties-should-not-be-strings"></a>CA1056：URI 屬性不應該為字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UriPropertiesShouldNotBeStrings|
|CheckId|CA1056|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型會宣告其名稱中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"的字串屬性。

## <a name="rule-description"></a>規則描述
 此規則會將屬性名稱分割為 pascal 命名法大小寫慣例為基礎的權杖，並檢查每個語彙基元是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，此規則會假設屬性代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri?displayProperty=fullName>類別會提供這些服務安全的方式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將屬性變更為<xref:System.Uri>型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果屬性不代表 URI。

## <a name="example"></a>範例
 下列範例顯示的型別`ErrorProne`，，違反這項規則和一個型別， `SaferWay`，符合規則。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)



