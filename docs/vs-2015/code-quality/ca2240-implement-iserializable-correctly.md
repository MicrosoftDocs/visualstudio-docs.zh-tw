---
title: CA2240 必須：正確地執行 ISerializable |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0abc95811dc870abbfaa583fbaa7705302a70781
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670161"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240：必須正確實作 ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見類型可指派給 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面，下列其中一個條件為 true：

- 型別會繼承，但不會覆寫 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法，而且型別會宣告未標記為 <xref:System.NonSerializedAttribute?displayProperty=fullName> 屬性的實例欄位。

- 型別不是密封的，而且型別會執行不是外部可見且可覆寫的 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法。

## <a name="rule-description"></a>規則描述
 在繼承 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面的型別中宣告的實例欄位，不會自動包含在序列化進程中。 若要包含欄位，類型必須執行 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法和序列化的函式。 如果欄位不應序列化，請將 <xref:System.NonSerializedAttribute> 屬性套用至欄位，以明確指出決策。

 在未密封的類型中，<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法的執行應該是外部可見的。 因此，方法可由衍生型別呼叫，而且可以覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法設為可見且可覆寫，並確定所有實例欄位都包含在序列化程式中，或明確地以 <xref:System.NonSerializedAttribute> 屬性標記。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則的可序列化類型。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例藉由提供 [ISerializable GetObjectData] 的覆寫執行，來修正先前的兩個違規（<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->）在 Book 類別上，並提供的執行 <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> 在 Library 類別上。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
