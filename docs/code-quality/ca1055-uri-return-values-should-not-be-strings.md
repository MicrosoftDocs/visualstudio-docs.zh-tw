---
title: CA1055:URI 傳回值不應該為字串
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1055
- UriReturnValuesShouldNotBeStrings
helpviewer_keywords:
- UriReturnValuesShouldNotBeStrings
- CA1055
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45d9874316ec2a22f875e2ba4fe7d5406ff916c6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547355"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055:URI 傳回值不應該為字串

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|Category|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法的名稱包含 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url", 而方法會傳回字串。

根據預設, 此規則只會查看公用方法, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

此規則會根據 Pascal 大小寫慣例, 將方法名稱分割成權杖, 並檢查每個權杖是否等於 "uri"、"Uri"、"urn"、"Urn"、"url" 或 "Url"。 如果相符, 此規則會假設方法會傳回統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri?displayProperty=fullName>類別以安全且安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形, 請將傳回型別<xref:System.Uri>變更為。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果傳回值不代表 URI, 則可以安全地隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是使用舊版分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分來執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 editorconfig 檔案:

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (設計) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示違反此規則的`ErrorProne`類型, 以及符合規則的`SaferWay`類型。

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>相關規則

- [CA1056URI 屬性不應為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054URI 參數不應為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234 必須傳遞 System.object 物件, 而不是字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057字串 URI 多載呼叫 System.object 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)