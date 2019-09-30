---
title: CA2237:ISerializable 類型必須標記 SerializableAttribute
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237933"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237:ISerializable 類型必須標記 SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
外部可見的類型會實<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>作為介面，而類型不會<xref:System.SerializableAttribute?displayProperty=fullName>以屬性標記。 此規則會忽略基底類型不可序列化的衍生類型。

## <a name="rule-description"></a>規則描述
若要由 common language runtime 辨識為可序列化，即使類型透過<xref:System.SerializableAttribute> <xref:System.Runtime.Serialization.ISerializable>介面的實作為使用自訂序列化常式，也必須以屬性標記類型。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將<xref:System.SerializableAttribute>屬性套用至類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿針對例外狀況類別隱藏此規則的警告，因為它們必須是可序列化的，才能在應用程式域間正常運作。

## <a name="example"></a>範例
下列範例顯示違反規則的類型。 取消批註<xref:System.SerializableAttribute>屬性行以符合規則。

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>相關規則
[CA2236 必須在 ISerializable 類型上呼叫基類方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240 必須正確地執行 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238:正確地執行序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239 必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120 必須安全序列化的函式](../code-quality/ca2120-secure-serialization-constructors.md)