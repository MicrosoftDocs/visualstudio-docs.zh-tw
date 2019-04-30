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
ms.openlocfilehash: 9ef3e012b3a818c60be23278fe622a40330f3b43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541476"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240:必須正確實作 ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

外部可見的類型是指派給<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面以及其中一個下列條件成立：

- 型別繼承，但不覆寫<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法和型別宣告與未標記的執行個體欄位<xref:System.NonSerializedAttribute?displayProperty=fullName>屬性。

- 不密封型別和型別實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>不是外部可見和可覆寫的方法。

## <a name="rule-description"></a>規則描述
 執行個體在繼承的類型中宣告的欄位<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面不會自動包含在序列化程序。 若要加入的欄位，類型必須實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化建構函式。 如果欄位不應該序列化，套用<xref:System.NonSerializedAttribute>屬性設為明確指出決策的欄位。

 在未密封的的實作類型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>應外部可見方法。 因此，方法可以由衍生型別、 呼叫，而且是可覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>可見和可覆寫的方法，並確定所有執行個體欄位會包含在序列化程序，或明確標示為<xref:System.NonSerializedAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則的可序列化型別。

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>範例
 下列範例會藉由提供的實作可以覆寫修正的兩個先前的違規情事<xref:System.Runtime.Serialization.ISerializable.GetObjectData>Book 類別和提供的實作`GetObjectData`程式庫類別上。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>相關的規則

- [CA2236： 必須ISerializable 類型上呼叫基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238： 請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237：Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239： 必須提供選擇性欄位的還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120： 必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)