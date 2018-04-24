---
title: CA1720：識別項不應包含類型名稱
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8a981dc4c8ccd016836ea55b2ecd624e781c5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720：識別項不應包含類型名稱
|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員中的參數名稱包含資料類型名稱。

 -或-

 外部可見成員的名稱包含語言特定的資料型別名稱。

## <a name="rule-description"></a>規則描述
 參數和成員的名稱最好用於傳達其意義說明其預期要由開發工具提供的類型。 名稱的成員，如果必須使用資料型別名稱，會使用與語言無關的名稱而不是特定語言。 比方說，而不是 C# 類型名稱 'int'，使用的語言無關的資料型別名稱，Int32。

 每個離散的權杖參數或成員的名稱不區分大小寫的方式被檢查對下列語言專屬的資料類型名稱：

-   Bool

-   WChar

-   Int8

-   UInt8

-   Short

-   UShort

-   Int

-   UInt

-   整數

-   UInteger

-   Long

-   ULong

-   不帶正負號

-   簽署人

-   浮動

-   Float32

-   Float64

 此外，參數的名稱也會簽對下列語言無關的資料類型名稱不區分大小寫的方式：

-   Object

-   obj

-   Boolean

-   Char

-   String

-   SByte

-   Byte

-   UByte

-   Int16

-   UInt16

-   Int32

-   UInt32

-   Int64

-   UInt64

-   IntPtr

-   Ptr

-   Pointer

-   UInptr

-   UPtr

-   UPointer

-   Single

-   Double

-   Decimal

-   Guid

## <a name="how-to-fix-violations"></a>如何修正違規
 **如果針對參數引發：**

 進一步描述其意義的詞彙或更泛型的詞彙如 'value' 取代參數名稱的資料類型識別項。

 **如果成員針對引發：**

 取代進一步描述其意義、 語言無關的同等權限或更泛型的詞彙如 'value' 的詞彙中的成員名稱的語言特定的資料類型識別項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 可能適合使用偶爾使用的類型為基礎的參數和成員的名稱。 不過，進行新開發，已知位置，您應該隱藏此規則的警告發生的狀況。 具有先前隨附的程式庫，您可能要隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719：參數名稱不應該和成員名稱相符](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)