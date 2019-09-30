---
title: CA2204:常值必須使用正確的拼字
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6763fd9f8999bd590511026f6571db6a747c43bc
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231849"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204:常值必須使用正確的拼字

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

常值字串會當做可當地語系化參數的引數，或當地語系化的屬性傳遞，而此字串包含一或多個 Microsoft 拼寫檢查程式庫無法辨識的文字。

## <a name="rule-description"></a>規則描述

當下列一或多個情況成立時，此規則會檢查當做值傳遞給參數或屬性的常值字串：

- 參數或屬性的屬性設定為true。<xref:System.ComponentModel.LocalizableAttribute>

- 參數或屬性名稱包含 "Text"、"Message" 或 "Caption"。

- 傳遞至<xref:System.Console.Write%2A>或<xref:System.Console.WriteLine>方法的字串變數名稱可以是 "value" 或 "format"。

此規則會將常值字串剖析成單字、token 化複合字組，並檢查每個單字或標記的拼寫。 如需剖析演算法的詳細資訊， [請參閱 CA1704：識別碼應該正確](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)拼寫。

## <a name="language"></a>語言

「拼寫檢查」目前只會針對以英文為基礎的文化特性字典進行檢查。 您可以藉由新增**CodeAnalysisCulture**元素，在專案檔中變更專案的文化特性。

例如：

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 如果您將文化特性設定為英文文化特性以外的任何專案，則會以無訊息模式停用此程式碼分析規則。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請更正單字的拼寫，或將此單字加入自訂字典。 如需如何使用自訂字典的詳細資訊[，請參閱如何：自訂程式碼分析](../code-quality/how-to-customize-the-code-analysis-dictionary.md)字典。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 拼寫正確的文字會減少新軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關規則

- [CA1704識別碼應該正確拼寫](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703資源字串的拼寫應該正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)