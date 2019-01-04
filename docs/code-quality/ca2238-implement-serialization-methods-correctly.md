---
title: CA2238:必須正確實作序列化方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5857892fb7e84e295a6d3f2a61fd67480a53c707
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834941"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238:必須正確實作序列化方法

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|分類|Microsoft.Usage|
|中斷變更|中斷-如果組件外部可見方法。<br /><br /> 非中斷-如果方法不是組件外部可見。|

## <a name="cause"></a>原因
 處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。

## <a name="rule-description"></a>規則描述
 方法所套用下列序列化事件屬性的其中一個指定的序列化事件處理常式：

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  序列化事件處理常式會接受單一參數型別的<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>、 return `void`，而且有`private`可見性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正簽章、 傳回型別或序列化的事件處理常式的可見性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會示範正確宣告的序列化事件處理常式。

 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA2236： 必須ISerializable 類型上呼叫基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235： 必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237： 必須Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239： 必須提供選擇性欄位的還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120： 必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)