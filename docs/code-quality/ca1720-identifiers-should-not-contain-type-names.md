---
title: CA1720:識別項名稱不應該包含類型名稱
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2677c2ef5342b795bb684f3ab06bc7cf5195cf7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233887"
---
# <a name="ca1720-identifiers-should-not-contain-type-names"></a>CA1720:識別項名稱不應該包含類型名稱

|||
|-|-|
|TypeName|IdentifiersShouldNotContainTypeNames|
|CheckId|CA1720|
|分類|Microsoft.Naming|
|重大變更|中斷|

## <a name="cause"></a>原因

成員中的參數名稱包含資料類型名稱。

-或-

成員的名稱包含特定語言的資料類型名稱。

根據預設，此規則只會查看外部可見的成員，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

參數和成員的名稱更適合用來傳達其意義，而不是描述其類型，這是開發工具應提供的。 對於成員的名稱，如果必須使用資料類型名稱，請使用與語言無關的名稱，而不是特定語言的名稱。 例如，而不是C#類型名稱`int`，請使用與語言無關的`Int32`資料類型名稱。

參數或成員名稱中的每個離散 token，會以不區分大小寫的方式，針對下列語言特定的資料類型名稱進行檢查：

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
- Guid

## <a name="how-to-fix-violations"></a>如何修正違規

**如果針對參數引發：**

將參數名稱中的資料類型識別碼取代為更清楚描述其意義的詞彙或更泛型的詞彙，例如 ' value '。

**如果是針對成員引發：**

將成員名稱中的語言特定資料類型識別碼取代為更清楚描述其意義的詞彙、與語言無關的對應，或更泛型的詞彙，例如 ' value '。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

偶爾使用以類型為基礎的參數和成員名稱可能是適當的。 不過，如果是新的開發，則不會發生任何已知案例，您應該在此隱藏此規則的警告。 針對先前已發行的程式庫，您可能必須隱藏此規則的警告。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1720.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（命名）來設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關規則

- [CA1709識別碼的大小寫應該正確](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708識別碼應該不同于大小寫](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707識別碼不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1719參數名稱不應與成員名稱相符](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)