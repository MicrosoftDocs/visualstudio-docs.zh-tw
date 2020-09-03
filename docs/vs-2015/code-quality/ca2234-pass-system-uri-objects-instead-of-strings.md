---
title: CA2234 必須：傳遞系統 Uri 物件，而不是字串 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ce5c076260886def089118a4d7211d75e0185c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545206"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234:必須傳遞 System.Uri 物件而非字串
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 對具有字串參數的方法進行呼叫，其名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url";方法的宣告型別包含具有參數的對應方法多載 <xref:System.Uri?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 參數名稱會根據 camel 大小寫慣例分割成權杖，然後檢查每個標記以查看它是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果有相符的參數，則會假設參數表示 (URI) 的統一資源識別項。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別以安全且安全的方式提供這些服務。 當兩個多載之間有一個差異，而這兩個多載只與 URI 的表示方式不同時，使用者應該選擇採用引數的多載 <xref:System.Uri> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請呼叫接受引數的多載 <xref:System.Uri> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果字串參數不代表 URI，則可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示違反規則的方法， `ErrorProne` 以及可正確呼叫多載的方法 `SaferWay` <xref:System.Uri> 。

 [!code-cpp[FxCop.Usage.PassUri#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cpp/FxCop.Usage.PassUri.cpp#1)]
 [!code-csharp[FxCop.Usage.PassUri#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/cs/FxCop.Usage.PassUri.cs#1)]
 [!code-vb[FxCop.Usage.PassUri#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PassUri/vb/FxCop.Usage.PassUri.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
