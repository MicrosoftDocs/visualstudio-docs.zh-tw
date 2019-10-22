---
title: CA1700：不要為保留&#39; &#39;的列舉值命名 |Microsoft Docs
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
ms.openlocfilehash: 9b5ddeb77a255bcfab121746cd8748c6fcb1f113
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669309"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700：不要為保留的列舉&#39;值命名&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉成員的名稱包含 "reserved" 這個字。

## <a name="rule-description"></a>規則描述
 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 您不應該希望使用者略過成員，因為它的名稱包含「已保留」，您也不能依賴使用者來閱讀或遵守檔。 此外，由於保留的成員會出現在物件瀏覽器和智慧型整合式開發環境中，因此可能會對實際使用的成員造成混淆。

 不使用保留成員，而是在未來版本的列舉中加入新成員。 在大多數情況下，加入新成員不是重大變更，只要加法不會造成原始成員的值變更。

 在有限的情況下，即使原始成員保留其原始值，新增成員也是一項重大變更。 主要而言，新成員無法從現有的程式碼路徑傳回，而不會中斷呼叫端（在包含整個成員清單的傳回值上使用 `switch` （`Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]）語句，而且會在預設情況下擲回例外狀況。 次要考慮是用戶端程式代碼可能不會處理反映方法（例如 <xref:System.Enum.IsDefined%2A?displayProperty=fullName>）行為的變更。 因此，如果新成員必須從現有的方法傳回，或已知的應用程式不相容，因為反映使用量不佳，則唯一不間斷的解決方案是：

1. 加入包含原始和新成員的新列舉。

2. 將原始列舉標記為 <xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性。

   針對任何外部可見的類型或公開原始列舉的成員，遵循相同的程式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名該成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 針對目前使用的成員或先前已發行的程式庫，隱藏此規則的警告是安全的。

## <a name="related-rules"></a>相關規則
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
