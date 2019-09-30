---
title: CA1700:不要為保留的列舉&#39;值命名&#39;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5171123827481c99bbc35c10b04aaf942a15fabb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234381"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700:不要為保留的列舉&#39;值命名&#39;

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|分類|Microsoft.Naming|
|重大變更|中斷|

## <a name="cause"></a>原因

列舉成員的名稱包含 "reserved" 這個字。

## <a name="rule-description"></a>規則描述

這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 您不應該希望使用者略過成員，因為它的名稱包含「已保留」，您也不能依賴使用者來閱讀或遵守檔。 此外，由於保留的成員會出現在物件瀏覽器和智慧型整合式開發環境中，因此可能會對實際使用的成員造成混淆。

不使用保留成員，而是在未來版本的列舉中加入新成員。 在大多數情況下，加入新成員不是重大變更，只要加法不會造成原始成員的值變更。

在有限的情況下，即使原始成員保留其原始值，新增成員也是一項重大變更。 主要而言，新成員無法從現有的程式碼路徑傳回，而不會中斷`switch`呼叫端[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]在包含整個成員清單並于中擲回例外狀況的呼叫端。`Select`預設案例。 次要考慮的是，用戶端程式代碼可能不會處理反映方法（例如） <xref:System.Enum.IsDefined%2A?displayProperty=fullName>的行為變更。 因此，如果新成員必須從現有的方法傳回，或已知的應用程式不相容，因為反映使用量不佳，則唯一不間斷的解決方案是：

1. 加入包含原始和新成員的新列舉。

2. 將原始列舉標記為<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性。

   針對任何外部可見的類型或公開原始列舉的成員，遵循相同的程式。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請移除或重新命名該成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

針對目前使用的成員或先前已發行的程式庫，隱藏此規則的警告是安全的。

## <a name="related-rules"></a>相關規則

[CA2217不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

[CA1712不要使用類型名稱做為列舉值的前置詞](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

[CA1028列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

[CA1008列舉的值應該為零](../code-quality/ca1008-enums-should-have-zero-value.md)

[CA1027 必須使用 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)