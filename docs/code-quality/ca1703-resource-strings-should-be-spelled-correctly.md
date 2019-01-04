---
title: CA1703:資源字串應該使用正確的拼字
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0458fa33413023fe9ae2b693a9bf75ffacda706c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890585"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703:資源字串應該使用正確的拼字

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|分類|Microsoft.Naming|
|中斷變更|非重大|

## <a name="cause"></a>原因

資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述

此規則會將資源字串剖析成單字 （token 化的複合字），並檢查每個字/語彙基元的拼字。 如需剖析演算法的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，使用完整的文字拼寫正確，或將文字加入自訂字典。 如需如何使用自訂字典的詳細資訊，請參閱[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="change-the-dictionary-language"></a>變更的字典語言

預設情況下，會使用英文 (en) 版本的拼字檢查程式。 如果您想要變更的拼字檢查程式語言，您可以這樣做加上下列其中一個屬性到您*AssemblyInfo.cs*或是*AssemblyInfo.vb*檔案：

- 使用<xref:System.Reflection.AssemblyCultureAttribute>指定的文化特性，如果您的資源位於附屬組件。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>來指定*中性文化特性*您組件，如果您的資源位於與您的程式碼相同的組件。

> [!IMPORTANT]
> 如果您將文化特性設定為以英文為基礎的文化特性以外的任何項目時，此程式碼分析規則是以無訊息模式停用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 正確拼寫的字會減少所需了解新的軟體程式庫的時間。

## <a name="related-rules"></a>相關的規則

- [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204:常值應該使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)