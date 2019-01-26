---
title: CA2229:必須實作序列化建構函式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 518a5d4f76d1c26893ae88f45bc74586654ee15c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951972"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229:必須實作序列化建構函式

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別實作<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面，不是委派或介面，其中下列條件成立：

- 類型不需要的建構函式<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>物件和<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>物件 （序列化建構函式的簽章）。

- 型別是密封和其序列化建構函式的存取修飾詞不是受保護 （系列）。

- 型別密封格式，其序列化建構函式的存取修飾詞不是私用。

## <a name="rule-description"></a>規則描述
 此規則是關於支援自訂序列化的類型。 類型支援的自訂序列化，如果它會實作<xref:System.Runtime.Serialization.ISerializable>介面。 序列化建構函式，才能還原序列化，或重新建立使用已序列化的物件<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏規則的違規情形。 型別將無法還原序列化，並在許多情況下將無法運作。

## <a name="example"></a>範例
 下列範例示範會滿足規則的類型。

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2237： 必須Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>