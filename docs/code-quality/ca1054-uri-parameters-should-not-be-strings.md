---
title: CA1054:URI 參數不應該為字串
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1054
- UriParametersShouldNotBeStrings
helpviewer_keywords:
- CA1054
- UriParametersShouldNotBeStrings
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 49788b900eb8aed9fac6e4da4844377bae67efbf
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235563"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054:URI 參數不應該為字串

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因

類型宣告了一個方法，其字串參數的名稱包含 "uri"、"uri"、"urn"、"urn"、"url" 或 "url"，而類型未宣告採用<xref:System.Uri?displayProperty=fullName>參數的對應多載。

根據預設，此規則只會查看外部可見的類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

此規則會根據 camel 大小寫慣例，將參數名稱分割成權杖，並檢查每個權杖是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果相符，此規則會假設參數代表統一資源識別元（URI）。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 如果方法接受 URI 的字串表示，則應提供對應的多載，以取得<xref:System.Uri>類別的實例，這會以安全且安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將參數變更<xref:System.Uri>為類型，這是一項重大變更。 或者，提供接受<xref:System.Uri>參數之方法的多載，這是不中斷的變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果參數不代表 URI，則可以安全地隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1054.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示違反此規則的`ErrorProne`類型，以及符合規則的`SaferWay`類型。

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>相關規則

- [CA1056URI 屬性不應為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1055URI 傳回值不應為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
- [CA2234 必須傳遞 System.object 物件，而不是字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057字串 URI 多載呼叫 System.object 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)