---
title: CA2240：必須正確實作 ISerializable
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9929937fa8655e5cbb4c86eebd4dce24fcb26966
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240：必須正確實作 ISerializable
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的類型是指派給<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面，以及其中一個的下列條件成立：

-   類型繼承，但不會覆寫<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法和類型宣告與未標記的執行個體欄位<xref:System.NonSerializedAttribute?displayProperty=fullName>屬性。

-   未密封的型別和型別實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>不是外部可見和可覆寫的方法。

## <a name="rule-description"></a>規則描述
 執行個體欄位在繼承的類型中宣告<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面未自動包含在序列化程序。 若要包含的欄位，類型必須實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法，並序列化建構函式。 如果欄位不應該序列化，套用<xref:System.NonSerializedAttribute>屬性設為明確指出決策的欄位。

 在未密封的的實作類型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>應為外部可見的方法。 因此，方法可以由衍生型別、 呼叫，而且是可覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>可見和可覆寫的方法，並確定所有執行個體欄位會包含在序列化程序，或明確地標示為與<xref:System.NonSerializedAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範兩個違反規則的可序列化型別。

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>範例
 下列範例將兩個先前的違規修正藉由提供可覆寫的實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData>書籍類別上，並藉由提供的實作`GetObjectData`程式庫類別上。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>相關的規則
 [Ca2236： 必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) [CA2229： 實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md) [CA2238： 正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md) [Ca2235： 必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md) [CA2237： 具有 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) [ca2239 必須： 提供還原序列化方法為選擇性欄位](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) [CA2120： 保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
