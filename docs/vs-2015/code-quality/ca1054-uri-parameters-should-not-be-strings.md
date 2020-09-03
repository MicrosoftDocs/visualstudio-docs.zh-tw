---
title: CA1054： URI 參數不應為字串 |Microsoft Docs
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
ms.openlocfilehash: babef652bbfa55d6549cf0e43ddae0920b3ff302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539486"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054:URI 參數不應該為字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別宣告了具有字串參數的方法，其名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"，且類型未宣告採用參數的對應多載 <xref:System.Uri?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 此規則會根據 camel 大小寫慣例，將參數名稱分割成權杖，並檢查每個權杖是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果有相符的規則，此規則會假設參數代表 (URI) 的統一資源識別項。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 如果方法採用 URI 的字串標記法，則應該提供對應的多載，以取得類別的實例 <xref:System.Uri> ，這會以安全且安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將參數變更為 <xref:System.Uri> 類型; 這是中斷性變更。 或者，提供接受參數之方法的多載， <xref:System.Uri> 這是不中斷的變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果參數不代表 URI，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的型別， `ErrorProne` 以及滿足規則的型別 `SaferWay` 。

 [!code-cpp[FxCop.Design.UriNotString#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cpp/FxCop.Design.UriNotString.cpp#1)]
 [!code-csharp[FxCop.Design.UriNotString#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/cs/FxCop.Design.UriNotString.cs#1)]
 [!code-vb[FxCop.Design.UriNotString#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UriNotString/vb/FxCop.Design.UriNotString.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234:必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
