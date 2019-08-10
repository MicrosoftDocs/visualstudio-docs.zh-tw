---
title: CA2240:必須正確實作 ISerializable
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1a6d9acc3a74505f766fbf9cfe26fc6878fdbb4b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920039"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240:必須正確實作 ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

外部可見類型可指派給<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面, 而下列其中一個條件為 true:

- 型別會繼承, 但不會<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>覆寫方法, 而且型別會宣告未<xref:System.NonSerializedAttribute?displayProperty=fullName>以屬性標記的實例欄位。

- 型別不是密封的, 而且型別<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>會實作為外部可見且可覆寫的方法。

## <a name="rule-description"></a>規則描述
在繼承<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面的類型中宣告的實例欄位不會自動包含在序列化進程中。 若要包含欄位, 類型必須執行<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化的函式。 如果欄位不應序列化, 請將<xref:System.NonSerializedAttribute>屬性套用至欄位, 以明確指出決策。

在未密封的類型中, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法的執行應該是外部可見的。 因此, 方法可由衍生型別呼叫, 而且可以覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法設為可見且可覆寫, 並確定所有實例欄位都包含在序列化程式中, <xref:System.NonSerializedAttribute>或明確地以屬性標示。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示兩個違反規則的可序列化類型。

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>範例
下列範例會藉由在 Book 類別<xref:System.Runtime.Serialization.ISerializable.GetObjectData>上提供的覆寫執行, 並在程式庫類別上提供的`GetObjectData`執行, 以修正前述的兩個違規。

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>相關規則

- [CA2236 必須在 ISerializable 類型上呼叫基類方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238:正確地執行序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239 必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)