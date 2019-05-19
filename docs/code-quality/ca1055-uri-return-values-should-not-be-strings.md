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
ms.openlocfilehash: 4517fc0d0dbfedc59a5a621f894d7e1d77b35c38
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842176"
---
# <a name="ca1055-uri-return-values-should-not-be-strings"></a>CA1055:URI 傳回值不應該為字串

|||
|-|-|
|TypeName|UriReturnValuesShouldNotBeStrings|
|CheckId|CA1055|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

方法的名稱包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"，而方法會傳回字串。

根據預設，此規則只會查看公用方法，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

此規則會將方法名稱分割為 pascal 命名法大小寫慣例為基礎的權杖，並檢查每個語彙基元是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，此規則假設方法會傳回統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri?displayProperty=fullName>類別會提供這些服務安全的方式。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將變更傳回型別，以<xref:System.Uri>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告，如果傳回的值不代表 URI。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1055.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例顯示的型別`ErrorProne`，，違反這項規則和一個型別， `SaferWay`，符合規則。

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>相關的規則

- [CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA2234： 必須必須傳遞 System.Uri 物件而不是字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)
- [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)