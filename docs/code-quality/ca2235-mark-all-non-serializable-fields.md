---
title: CA2235:必須標記所有不可序列化的欄位
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238108"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235:必須標記所有不可序列化的欄位

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。

## <a name="rule-description"></a>規則描述

可序列化型別是以<xref:System.SerializableAttribute?displayProperty=fullName>屬性標記的類型。 當型別序列化時，如果<xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName>型別包含不可序列化*且*不會執行<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面之型別的實例欄位，就會擲回例外狀況（exception）。

> [!TIP]
> 針對實作為類型的實例欄位，不會引發<xref:System.Runtime.Serialization.ISerializable> ca2235 必須，因為它們會提供自己的序列化邏輯。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請<xref:System.NonSerializedAttribute?displayProperty=fullName>將屬性套用至不可序列化的欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果宣告的<xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>類型允許將欄位的實例序列化和還原序列化，則只會隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示兩種類型：一個違反規則，另一個符合規則。

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>備註

規則 ca2235 必須不會分析實作為<xref:System.Runtime.Serialization.ISerializable>介面的<xref:System.SerializableAttribute>型別（除非它們也會以屬性標記）。 這是因為[規則 ca2237 必須](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)已經建議使用<xref:System.SerializableAttribute>屬性（attribute） <xref:System.Runtime.Serialization.ISerializable>來執行介面的標記類型。

## <a name="related-rules"></a>相關規則

- [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236 必須在 ISerializable 類型上呼叫基類方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238:正確地執行序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239 必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240 必須正確地執行 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)