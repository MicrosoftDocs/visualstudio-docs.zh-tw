---
title: CA1700：請勿將列舉值命名 &#39;保留&#39; |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 57f2a2e5959860a99a921101ff5782f9bce9ace3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545648"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700：請勿將列舉值命名 &#39;保留&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉成員的名稱包含 "reserved" 這個字。

## <a name="rule-description"></a>規則描述
 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 您不應該希望使用者略過成員，因為它的名稱包含「已保留」，您也不能依賴使用者來閱讀或遵守檔。 此外，由於保留的成員會出現在物件瀏覽器和智慧型整合式開發環境中，因此可能會對實際使用的成員造成混淆。

 不使用保留成員，而是在未來版本的列舉中加入新成員。 在大多數情況下，加入新成員不是重大變更，只要加法不會造成原始成員的值變更。

 在有限的情況下，即使原始成員保留其原始值，新增成員也是一項重大變更。 主要是新成員無法從現有的程式碼路徑傳回，而不會中斷呼叫端在 `switch` `Select` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 包含整個成員清單並在預設案例中擲回例外狀況的呼叫端使用（in）語句。 次要考慮的是，用戶端程式代碼可能不會處理反映方法（例如）的行為變更 <xref:System.Enum.IsDefined%2A?displayProperty=fullName> 。 因此，如果新成員必須從現有的方法傳回，或已知的應用程式不相容，因為反映使用量不佳，則唯一不間斷的解決方案是：

1. 加入包含原始和新成員的新列舉。

2. 將原始列舉標記為 <xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性。

   針對任何外部可見的類型或公開原始列舉的成員，遵循相同的程式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名該成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對目前使用的成員或先前已發行的程式庫，隱藏此規則的警告是安全的。

## <a name="related-rules"></a>相關規則
 [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008:列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
