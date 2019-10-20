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
ms.openlocfilehash: 34ebe4848bbbe49b9a67449795f0aea7d104af8b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671631"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720：識別項不應包含類型名稱
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|Category|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見成員中的參數名稱包含資料類型名稱。

 -或-

 外部可見成員的名稱包含特定語言的資料類型名稱。

## <a name="rule-description"></a>規則描述
 參數和成員的名稱更適合用來傳達其意義，而不是描述其類型，這是開發工具應提供的。 對於成員的名稱，如果必須使用資料類型名稱，請使用與語言無關的名稱，而不是特定語言的名稱。 例如，不是C#型別名稱 ' int '，而是使用與語言無關的資料型別名稱 Int32。

 參數或成員名稱中的每個離散 token 都會根據下列特定語言的資料類型名稱，以不區分大小寫的方式進行檢查：

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

- Long

- ULong

- 不帶正負號

- 簽署人

- 浮動

- Float32

- Float64

  此外，也會以不區分大小寫的方式，針對下列與語言無關的資料類型名稱，檢查參數的名稱：

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

- 指標

- Pointer

- UInptr

- UPtr

- UPointer

- Single

- Double

- Decimal

- GUID

## <a name="how-to-fix-violations"></a>如何修正違規
 **如果針對參數引發：**

 將參數名稱中的資料類型識別碼取代為更清楚描述其意義的詞彙或更泛型的詞彙，例如 ' value '。

 **如果是針對成員引發：**

 將成員名稱中的語言特定資料類型識別碼取代為更清楚描述其意義的詞彙、與語言無關的對應，或更泛型的詞彙，例如 ' value '。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 偶爾使用以類型為基礎的參數和成員名稱可能是適當的。 不過，如果是新的開發，則不會發生任何已知案例，您應該在此隱藏此規則的警告。 針對先前隨附的程式庫，您可能必須隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1719：參數名稱不應該和成員名稱相符](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)
