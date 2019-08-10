---
title: CA2236:必須呼叫 ISerializable 類型上的基底類別方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f0075a6296e839030448c0209c77f1717a5fcb1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920128"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236:必須呼叫 ISerializable 類型上的基底類別方法

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
型別衍生自實<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面的型別, 而下列其中一個條件為 true:

- 型別會實作為序列化的函式, 也就是具有<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>、 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>參數簽章的函式, 但不會呼叫基底型別的序列化函式。

- 類型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>會執行方法, 但不會呼叫基<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>底類型的方法。

## <a name="rule-description"></a>規則描述
在自訂序列化程式中, 型別會<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>實作為序列化其欄位的方法, 以及將欄位還原序列化的序列化函式。 如果類型衍生自實<xref:System.Runtime.Serialization.ISerializable>介面的類型, 則應該呼叫基底類型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化的函式, 以序列化/還原序列化基底類型的欄位。 否則, 類型將不會正確地序列化和還原序列化。 請注意, 如果衍生的型別不會加入任何新的欄位, 則型別不需要<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>實作為方法, 也不會呼叫基底型別的對等專案。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請從對應的<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>衍生類型方法或函式呼叫基底類型方法或序列化的函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例會藉由呼叫基類的序列化函式和<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法, 顯示符合規則的衍生型別。

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2240 必須正確地執行 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238:正確地執行序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239 必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)