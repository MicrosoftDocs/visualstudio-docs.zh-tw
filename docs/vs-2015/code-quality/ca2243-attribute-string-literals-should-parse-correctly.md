---
title: CA2243:屬性字串常值必須正確剖析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f23db8a9674de621090be70067a555ef4fca2b99
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061419"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243:屬性字串常值必須正確剖析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 屬性的字串常值參數不會正確剖析 URL、 GUID 或版本。

## <a name="rule-description"></a>規則描述
 因為屬性衍生自<xref:System.Attribute?displayProperty=fullName>，屬性用在編譯時期，只有常值可以傳遞至其建構函式。 必須在 Url、 Guid 和版本所代表的屬性參數類型不可以是<xref:System.Uri?displayProperty=fullName>， <xref:System.Guid?displayProperty=fullName>，和<xref:System.Version?displayProperty=fullName>，因為這些類型無法表示為常數。 相反地，必須以字串表示。

 因為參數類型為字串，就可以在編譯時期，無法傳遞的格式不正確的參數。

 此規則會使用命名的啟發學習法，找出代表統一資源識別元 (URI)，全域唯一識別碼 (GUID) 或版本的參數，並確認傳遞的值正確無誤。

## <a name="how-to-fix-violations"></a>如何修正違規
 將參數字串變更為格式正確的 URL、 GUID 或版本。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果參數不代表 URL、 GUID 或版本。

## <a name="example"></a>範例
 下列範例顯示 AssemblyFileVersionAttribute 違反此規則的程式碼。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 此規則會觸發下列：

- 參數會包含 'version'，而且無法剖析為 System.Version。

- 參數會包含 [guid]，而且無法剖析為 System.Guid。

- 參數會包含 'uri'、 'urn' 或 'url'，而且無法剖析為 System.Uri。

## <a name="see-also"></a>另請參閱
 [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
