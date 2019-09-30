---
title: CA1703:資源字串應該使用正確的拼字
ms.date: 03/28/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234316"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703:資源字串應該使用正確的拼字

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|分類|Microsoft.Naming|
|重大變更|不中斷|

## <a name="cause"></a>原因

資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。

## <a name="rule-description"></a>規則描述

此規則會將資源字串剖析成單字（token 化的複合字組），並檢查每個單字/token 的拼寫。 如需剖析演算法的詳細資訊， [請參閱 CA1704：識別碼應該正確](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)拼寫。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用正確拼寫的完整單字，或將單字加入自訂字典。 如需如何使用自訂字典的詳細資訊[，請參閱 CA1704：識別碼應該正確](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)拼寫。

## <a name="change-the-dictionary-language"></a>變更字典語言

根據預設，會使用拼寫檢查的英文（en）版本。 如果您想要變更拼寫檢查的語言，您可以將下列其中一個屬性新增至*AssemblyInfo.cs*或*AssemblyInfo .vb*檔案來執行此動作：

- 如果<xref:System.Reflection.AssemblyCultureAttribute>您的資源是在附屬元件中，請使用來指定文化特性。
- 如果<xref:System.Resources.NeutralResourcesLanguageAttribute>您的資源與您的程式碼位於相同的元件，請使用來指定元件的*中性文化*特性。

> [!IMPORTANT]
> 如果您將文化特性設定為英文文化特性以外的任何專案，則會以無訊息模式停用此程式碼分析規則。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 拼寫正確的文字會減少學習新軟體程式庫所需的時間。

## <a name="related-rules"></a>相關規則

- [CA1701資源字串複合字應該是正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704識別碼應該正確拼寫](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204常值的拼寫應該正確](../code-quality/ca2204-literals-should-be-spelled-correctly.md)