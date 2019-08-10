---
title: CA2239:必須為選擇性欄位提供還原序列化方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c0cd59ec30ce45c94ac3422c4271959d74073bff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920055"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239:必須為選擇性欄位提供還原序列化方法

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
型別具有以<xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>屬性標記的欄位, 而且型別不提供還原序列化事件處理方法。

## <a name="rule-description"></a>規則描述
<xref:System.Runtime.Serialization.OptionalFieldAttribute>屬性不會影響序列化; 以屬性標記的欄位會序列化。 不過, 還原序列化時會忽略欄位, 並保留與其類型相關聯的預設值。 還原序列化的事件處理常式應該宣告為在還原序列化過程中設定欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將還原序列化事件處理方法加入至類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果在還原序列化程式期間應該忽略欄位, 則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示具有選擇性欄位和還原序列化事件處理方法的類型。

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>相關規則
[CA2236 必須在 ISerializable 類型上呼叫基類方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 必須正確地執行 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238:正確地執行序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)