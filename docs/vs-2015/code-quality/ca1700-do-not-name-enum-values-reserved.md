---
title: CA1700： 不要在列舉值名稱&#39;保留&#39;|Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7aaab7f774b274b9e70efac404d1ab4ba3315d93
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588492"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700： 不要在列舉值名稱&#39;保留&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1700： 不要在列舉值名稱&#39;保留&#39;](https://docs.microsoft.com/visualstudio/code-quality/ca1700-do-not-name-enum-values-reserved)。

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉成員的名稱包含 「 保留 」 這個字。

## <a name="rule-description"></a>規則描述
 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 您不應該預期使用者會忽略該成員，因為其名稱包含 「 保留 」，也不能依賴使用者讀取或遵守文件。 此外，保留的成員會出現在物件瀏覽器和智慧型整合的開發環境，因為它們可能會導致的混淆哪些成員實際上都使用。

 不使用保留的成員，將新成員加入列舉未來的版本。 在大部分情況下加入新不是成員的重大變更，只要新增不會造成要變更之原始成員值。

 在少數情況下加入成員的原始成員保留其原始值時，即使是一項重大變更。 主要，新的成員無法傳回從現有的程式碼路徑而不會中斷使用的呼叫端`switch`(`Select`在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 傳回的值，包含整個成員清單，並會在擲回例外狀況的陳述式預設的情況。 次要的問題是，用戶端程式碼可能無法處理，反映方法的行為變更例如<xref:System.Enum.IsDefined%2A?displayProperty=fullName>。 因此，如果新的成員都有要從現有的方法傳回或已知的應用程式不相容，就會發生因為不佳的反映，唯一不中斷的解決方案是：

1.  加入新的列舉，其中包含的原始和新成員。

2.  標記的原始列舉<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性。

 請遵循相同的程序的任何外部可見類型或公開原始列舉的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除或重新命名的成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，目前使用的成員或是先前所提供的程式庫。

## <a name="related-rules"></a>相關的規則
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)



