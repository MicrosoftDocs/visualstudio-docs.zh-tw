---
title: CA1054：URI 參數不應該為字串
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 740a3354b9b14bb62dee259c6534ce8065162894
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900026"
---
# <a name="ca1054-uri-parameters-should-not-be-strings"></a>CA1054：URI 參數不應該為字串
|||
|-|-|
|TypeName|UriParametersShouldNotBeStrings|
|CheckId|CA1054|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型會宣告具有其名稱中包含"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"的字串參數的方法和類型並不會宣告對應的多載採用<xref:System.Uri?displayProperty=fullName>參數。

## <a name="rule-description"></a>規則描述
 此規則會分割成語彙基元的 camel 命名法的大小寫慣例為基礎的參數名稱，並檢查每個語彙基元是否等於"uri"、"Uri"、"urn"、"Urn"、"url"或"Url"。 如果沒有相符項目，此規則會假設此參數代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 如果方法使用 URI 的字串表示，對應的多載應該提供採用的執行個體<xref:System.Uri>類別，以安全的方式提供這些服務。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將參數變更為<xref:System.Uri>輸入; 這是一項重大變更。 或者，提供多載的方法會採用<xref:System.Uri>參數; 這是不中斷變更。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果參數不代表 URI。

## <a name="example"></a>範例
 下列範例顯示型別， `ErrorProne`，違反這項規則，以及類型， `SaferWay`，符合此規則。

 [!code-csharp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]

## <a name="related-rules"></a>相關的規則
 [CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)

 [CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)