---
title: CA1700： 不要在列舉值名稱&#39;保留&#39;
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2e7b501019ed2891a30d1f0359aee6405c4444
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700： 不要在列舉值名稱&#39;保留&#39;
|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 列舉成員的名稱包含 「 保留 」 這個字。

## <a name="rule-description"></a>規則描述
 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 您不應預期使用者會忽略該成員，因為其名稱包含 「 保留 」，也不能依賴使用者讀取或遵守文件。 此外，由於保留的成員會顯示在物件瀏覽器和智慧型整合的開發環境中，它們可能造成的混淆的成員會實際正在使用。

 不要使用保留的成員，將新成員加入未來版本中列舉。 在大部分情況下加入新成員不是一項重大變更，只要加入不會造成要變更之原始成員的值。

 在少數的情況下加入成員是中斷變更，即使原始成員保留其原始值。 主要是新的成員不能傳回從現有的程式碼路徑而不會中斷使用的呼叫端`switch`(`Select`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 傳回的值，包含整個成員清單，並會在擲回例外狀況的陳述式預設的情況。 次要的問題是，用戶端程式碼可能不處理反映方法的行為變更例如<xref:System.Enum.IsDefined%2A?displayProperty=fullName>。 因此，若已從現有的方法傳回的新成員，或因為不佳的反映已知的應用程式不相容，唯一不分行解決方法是：

1.  加入新的列舉，其中包含原始和新的成員。

2.  將標記與在原始列舉<xref:System.ObsoleteAttribute?displayProperty=fullName>屬性。

 請遵循相同的程序的任何外部可見類型或公開原始列舉的成員。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除或重新命名的成員。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告目前使用的成員或是先前所提供的程式庫。

## <a name="related-rules"></a>相關的規則
 [CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712：不要使用類型名稱做為列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)