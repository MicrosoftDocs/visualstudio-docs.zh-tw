---
title: CA2243:屬性字串常值必須正確剖析
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c0f078c21de023b1f5cfacde0cf122c179adb2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919908"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243:屬性字串常值必須正確剖析

|||
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
屬性的字串常值參數無法正確剖析 URL、GUID 或版本。

## <a name="rule-description"></a>規則描述
因為屬性是衍生自<xref:System.Attribute?displayProperty=fullName>, 而且屬性是在編譯時期使用, 所以只有常數值可以傳遞至其函式。 必須代表 url、guid 和版本的屬性參數不可以輸入為<xref:System.Uri?displayProperty=fullName>、 <xref:System.Guid?displayProperty=fullName>和<xref:System.Version?displayProperty=fullName>, 因為這些類型不能表示為常數。 相反地, 它們必須以字串表示。

因為參數的類型是字串, 所以可能會在編譯時期傳遞格式不正確的參數。

此規則使用命名啟發學習法來尋找代表統一資源識別元 (URI)、全域唯一識別碼 (GUID) 或版本的參數, 並確認傳遞的值是否正確。

## <a name="how-to-fix-violations"></a>如何修正違規
將參數字串變更為正確格式的 URL、GUID 或版本。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果參數不代表 URL、GUID 或版本, 就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例會顯示違反此規則的 AssemblyFileVersionAttribute 程式碼。

[!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]

此規則是由下列參數所觸發:

- 包含 ' version ' 且無法剖析為 System.object 的參數。

- 包含 ' guid ' 且無法剖析為 Guid.empty 的參數。

- 包含 ' uri '、' urn ' 或 ' url ' 的參數無法剖析為 system.string。

## <a name="see-also"></a>另請參閱

- [CA1054URI 參數不應為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)