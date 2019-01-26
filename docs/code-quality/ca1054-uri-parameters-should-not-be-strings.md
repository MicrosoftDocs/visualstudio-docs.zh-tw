---
title: CA1054:URI 參數不應該為字串
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 7903e5f5241dabecc8077f4c56148c6ac40f5518
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018848"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054:URI 參數不應該為字串

|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

型別會宣告具有其名稱中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"的字串參數的方法和型別並不會宣告對應的多載，<xref:System.Uri?displayProperty=fullName>參數。

## <a name="rule-description"></a>規則描述

此規則會將參數名稱分割成駝峰式命名法大小寫慣例為基礎的權杖，並檢查每個語彙基元是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，此規則會假設參數表示的統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 方法會採用 URI 的字串表示，如果對應的多載應該提供採用的執行個體<xref:System.Uri>類別，可在安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將參數變更為<xref:System.Uri>類型; 這是一項重大變更。 或者，提供可採用的方法多載<xref:System.Uri>參數; 這是不間斷的變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它會安全地隱藏此規則的警告，如果參數不代表 URI。

## <a name="example"></a>範例

下列範例顯示的型別`ErrorProne`，，違反這項規則和一個型別， `SaferWay`，符合規則。

[!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
[!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
[!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>相關的規則

[CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

[CA1055:URI 會傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

[CA2234： 必須必須傳遞 System.Uri 物件而不是字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

[CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)