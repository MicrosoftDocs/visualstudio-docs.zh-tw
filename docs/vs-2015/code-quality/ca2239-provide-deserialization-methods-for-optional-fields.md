---
title: CA2239 必須：為選擇性欄位提供還原序列化方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfbb9082d557c8e67ddebf0237293364d54a65cf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545128"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239:必須為選擇性欄位提供還原序列化方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別具有以屬性標記的欄位 <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> ，而且型別不提供還原序列化事件處理方法。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>屬性不會影響序列化; 以屬性標記的欄位會序列化。 不過，還原序列化時會忽略欄位，並保留與其類型相關聯的預設值。 還原序列化的事件處理常式應該宣告為在還原序列化過程中設定欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將還原序列化事件處理方法加入至類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果在還原序列化程式期間應該忽略欄位，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示具有選擇性欄位和還原序列化事件處理方法的類型。

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2236:必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229:必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238:必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235:必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237:ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120:必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
