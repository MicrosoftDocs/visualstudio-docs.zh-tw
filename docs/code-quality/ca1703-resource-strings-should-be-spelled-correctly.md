---
title: CA1703： 資源字串應該拼寫正確 |Microsoft 文件
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1227849992cf91a208563020583b19af48b13d42
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2018
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703：資源字串應該拼寫正確

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|分類|Microsoft.Naming|
|中斷變更|非中斷|

## <a name="cause"></a>原因

資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述

此規則的資源字串剖析成單字 (token 複合字)，並檢查每個字/語彙基元的拼字。 剖析演算法的相關資訊，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用完整文字拼寫正確，或將單字加入到自訂字典。 如需如何使用自訂字典，請參閱[CA1704： 識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)。

## <a name="change-the-dictionary-language"></a>變更的字典語言

根據預設，會使用拼字檢查程式的英文 (en) 版。 如果您想要變更的拼字檢查程式語言，您可以藉由新增下列其中一種屬性，將因此您*AssemblyInfo.cs*或*AssemblyInfo.vb*檔案：

- 使用<xref:System.Reflection.AssemblyCultureAttribute>指定文化特性，如果您的資源的附屬組件中。
- 使用<xref:System.Resources.NeutralResourcesLanguageAttribute>指定*中性文化特性*如果資源位於相同的組件程式碼組件。

> [!IMPORTANT]
> 如果您將文化特性設定為英文的文化特性以外的任何項目時，此程式碼分析規則以無訊息模式已停用。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 正確拼寫正確的單字會減少學習新的軟體程式庫的時間。

## <a name="related-rules"></a>相關的規則

- [CA1701：資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704：識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)