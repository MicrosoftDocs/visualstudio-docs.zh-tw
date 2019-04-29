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
ms.openlocfilehash: 82146c2ac997a0202c20e15492becb89a293f427
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541919"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204:常值必須使用正確的拼字

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

常值的字串會傳遞做為引數是可當地語系化的參數，或可當地語系化的屬性，以及字串包含一或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述

此規則會檢查常值字串做為值傳遞至參數或屬性，當一或多個下列情況為 true:

- <xref:System.ComponentModel.LocalizableAttribute>參數或屬性的屬性設定為 true。

- 參數或屬性名稱中包含 「 文字 」、 「 訊息 」，或 「 標題 」。

- 傳遞至字串變數的名稱<xref:System.Console.Write%2A>或<xref:System.Console.WriteLine>方法為"value"format"。

此規則會將常值字串剖析成單字、 token 化複合字，並檢查每個字組 」 或 「 語彙基元的拼字。 如需剖析演算法的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="language"></a>語言

拼字檢查工具目前會檢查只會針對英文版為基礎的文化特性的字典。 您可以加入，以變更您的專案在專案檔中的文化特性**CodeAnalysisCulture**項目。

例如：

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> 如果您將文化特性設定為以英文為基礎的文化特性以外的任何項目時，此程式碼分析規則是以無訊息模式停用。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，更正這個字的拼字，或將該字加入至自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[How to:自訂程式碼分析字典](../code-quality/how-to-customize-the-code-analysis-dictionary.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 正確拼寫的字會減少新的軟體程式庫所需的學習曲線。

## <a name="related-rules"></a>相關的規則

- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)