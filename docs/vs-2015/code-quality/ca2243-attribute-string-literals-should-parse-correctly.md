---
title: CA2243：屬性字串常值應該正確地剖析 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 09e932651576f9b6d595657ad024b8f2697ad016
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535742"
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243:屬性字串常值必須正確剖析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AttributeStringLiteralsShouldParseCorrectly|
|CheckId|CA2243|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 屬性的字串常值參數未正確剖析 URL、GUID 或版本。

## <a name="rule-description"></a>規則描述
 由於屬性是衍生自 <xref:System.Attribute?displayProperty=fullName> ，而且在編譯時期會使用屬性，因此只能將常數值傳遞給其函式。 必須代表 Url、Guid 和版本的屬性參數不能輸入為 <xref:System.Uri?displayProperty=fullName> 、 <xref:System.Guid?displayProperty=fullName> 和 <xref:System.Version?displayProperty=fullName> ，因為這些類型無法表示為常數。 相反地，它們必須以字串表示。

 因為參數的類型為字串，所以可能會在編譯時期傳遞格式不正確的參數。

 這項規則會使用命名法來尋找表示統一資源識別項的參數， (URI) 、全域唯一識別碼 (GUID) 或版本，並驗證傳遞的值是否正確。

## <a name="how-to-fix-violations"></a>如何修正違規
 將參數字串變更為正確格式的 URL、GUID 或版本。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果參數不代表 URL、GUID 或版本，就可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示違反此規則之 AssemblyFileVersionAttribute 的程式碼。

 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly/cs/FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly.cs#1)]

 此規則會由下列程式觸發：

- 包含 ' version ' 且無法剖析為 System.object 的參數。

- 包含 ' guid ' 且無法剖析為 Guid.empty 的參數。

- 包含 ' uri '、' urn ' 或 ' url ' 且無法剖析為 system.string 的參數。

## <a name="see-also"></a>另請參閱
 [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
