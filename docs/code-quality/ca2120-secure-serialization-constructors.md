---
title: CA2120:必須保護序列化建構函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15fd1596fdede3d13d603e7df222395a7ef7a277
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545110"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120:必須保護序列化建構函式

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別實作<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面不是委派或介面，以及允許部分信任呼叫端的組件中宣告。 類型具有的建構函式<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>物件和<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>物件 （序列化建構函式的簽章）。 這個建構函式未受到安全性檢查，但一或多個型別中的一般建構函式會受到保護。

## <a name="rule-description"></a>規則描述
 此規則是關於支援自訂序列化的類型。 類型支援的自訂序列化，如果它會實作<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面。 序列化建構函式需要與用來還原序列化，或重新建立使用已序列化的物件<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法。 因為序列化建構函式會配置並初始化物件，也必須存在於上序列化建構函式都存在於規則建構函式的安全性檢查。 如果您違反此規則，否則不可能建立執行個體的呼叫端可以使用序列化建構函式若要這樣做。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，保護序列化建構函式與保護其他建構函式完全相同的安全性需求。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏規則的違規情形。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237：Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>