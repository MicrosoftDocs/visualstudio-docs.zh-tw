---
title: CA2235 必須：標記所有非可序列化的欄位 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fab79fd4daab98c6cade9271b32c45b5ae4b4332
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545193"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235:必須標記所有不可序列化的欄位
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。

## <a name="rule-description"></a>規則描述
 可序列化型別是以屬性標記的類型 <xref:System.SerializableAttribute?displayProperty=fullName> 。 當類型序列化時， <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> 如果類型包含無法序列化之類型的實例欄位，則會擲回例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性套用至不可序列化的 <xref:System.NonSerializedAttribute?displayProperty=fullName> 欄位。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果宣告 <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> 的類型允許將欄位的實例序列化和還原序列化，則只會隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型，以及符合規則的類型。

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2236:必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240:必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229:必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238:必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237:ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239:必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120:必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
