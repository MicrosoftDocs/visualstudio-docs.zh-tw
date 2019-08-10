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
ms.openlocfilehash: dc7f4a82b9a75e4d189e969712472f06b4019b73
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920873"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120:必須保護序列化建構函式

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
型別會實<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>作為介面, 不是委派或介面, 而且會在允許部分信任呼叫端的元件中宣告。 型別具有接受<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>物件<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>和物件的函式 (序列化函式的簽章)。 此函式不會受到安全性檢查的保護, 但類型中的一或多個一般函式會受到保護。

## <a name="rule-description"></a>規則描述
此規則與支援自訂序列化的類型有關。 類型支援自訂序列化 (如果它會<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>執行介面)。 序列化的函式是必要的, 可用來還原序列化或重新建立已使用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法序列化的物件。 因為序列化的函式會配置並初始化物件, 所以在一般的函式上出現的安全性檢查也必須存在於序列化的函式上。 如果您違反此規則, 無法以其他方式建立實例的呼叫端可以使用序列化的函式來執行此動作。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請使用與保護其他的處理常式相同的安全性要求來保護序列化的函數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏規則的違規。

## <a name="example"></a>範例
下列範例顯示違反規則的類型。

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>