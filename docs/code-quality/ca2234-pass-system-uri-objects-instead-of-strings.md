---
title: CA2234:必須傳遞 System.Uri 物件而非字串
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6e7f333ae6f9e938261c0f91196120f3376d0388
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841591"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234:必須傳遞 System.Uri 物件而非字串

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

呼叫的方法有其名稱中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"的字串參數和方法的宣告型別包含對應的方法多載具有<xref:System.Uri?displayProperty=fullName>參數。

根據預設，此規則只會查看外部可見的方法和型別，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

參數名稱會分割成駝峰式命名法大小寫慣例為基礎的權杖，然後每個語彙基元會檢查以查看它是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，則參數會假設代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 <xref:System.Uri>類別會提供這些服務安全的方式。 使用者之間的差異只關於 URI 的表示法的兩個多載有所選擇，應該選擇採用的多載<xref:System.Uri>引數。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請呼叫採用的多載<xref:System.Uri>引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告，如果字串參數不代表 URI。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca2234.api_surface = private, internal
```

您可以設定此選項只是這項規則，所有規則，或所有規則 （使用） 這個類別中。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example"></a>範例

下列範例示範的方法中， `ErrorProne`，，違反規則和方法， `SaferWay`，它會正確地呼叫<xref:System.Uri>多載：

[!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
[!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
[!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)
- [CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)
- [CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)
- [CA1055:URI 會傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)