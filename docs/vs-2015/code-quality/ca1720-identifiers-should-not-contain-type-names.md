---
title: CA1720：識別碼不應包含類型名稱 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1720
- IdentifiersShouldNotContainTypeNames
helpviewer_keywords:
- IdentifiersShouldNotContainTypeNames
- CA1720
ms.assetid: c95ee48f-f23a-45f0-ac9e-a3c1ecfabdea
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f6d228b0fbf5507ba135f9ddc35d6d8b161f0011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534845"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720:識別項名稱不應該包含類型名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員中的參數名稱包含資料類型名稱。

 -或-

 外部可見成員的名稱包含特定語言的資料類型名稱。

## <a name="rule-description"></a>規則描述
 參數和成員的名稱較適合用來傳達其意義，而不是描述其型別，其預期是由開發工具提供。 對於成員的名稱，如果必須使用資料類型名稱，請使用與語言無關的名稱，而不是特定語言的名稱。 例如，而不是使用 c # 型別名稱 ' int '，請使用與語言無關的資料類型名稱 Int32。

 參數或成員名稱中的每個離散 token 都會以不區分大小寫的方式，針對下列特定語言的資料類型名稱進行檢查：

- Bool

- WChar

- Int8

- UInt8

- Short

- UShort

- Int

- UInt

- 整數

- UInteger

- long

- ULong

- 不帶正負號

- 簽署人

- Float

- Float32

- Float64

  此外，也會以不區分大小寫的方式，檢查參數的名稱是否符合下列與語言無關的資料類型名稱：

- Object

- Obj

- Boolean

- Char

- String

- SByte

- Byte

- UByte

- Int16

- UInt16

- Int32

- UInt32

- Int64

- UInt64

- IntPtr

- Ptr

- Pointer

- UInptr

- UPtr

- UPointer

- 單一

- Double

- 小數位數

- Guid

## <a name="how-to-fix-violations"></a>如何修正違規
 **若針對參數引發：**

 將參數名稱中的資料類型識別碼取代為可進一步描述其意義或更泛型詞彙的詞彙，例如 ' value '。

 **如果針對成員引發：**

 以更清楚描述其意義的詞彙、與語言無關的相等或更泛型的詞彙（例如 ' value '）取代成員名稱中的語言特定資料類型識別碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 偶爾使用以型別為基礎的參數和成員名稱可能是適當的。 不過，對於新的開發，不會發生任何已知案例，因此您應該隱藏此規則的警告。 針對先前隨附的程式庫，您可能必須隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707:識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719:參數名稱不應該和成員名稱相符](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
