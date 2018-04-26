---
title: CA2239：必須為選擇性欄位提供還原序列化方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04d3e40c73a02c43ecfb13eda0abcfabcb0d3ad5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239：必須為選擇性欄位提供還原序列化方法
|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 類型具有標示為欄位<xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>屬性和型別不提供還原序列化事件處理方法。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>屬性沒有任何作用，進行序列化時，會序列化以屬性標記的欄位。 不過，欄位會忽略在還原序列化，並會保留它的型別相關聯的預設值。 還原序列化事件處理常式應該要在還原序列化程序期間設定欄位宣告。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，新增還原序列化事件處理方法的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告，如果在還原序列化程序期間，應該忽略欄位。

## <a name="example"></a>範例
 下列範例顯示具有選擇性欄位和還原序列化事件的型別處理方法。

 [!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240：必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)