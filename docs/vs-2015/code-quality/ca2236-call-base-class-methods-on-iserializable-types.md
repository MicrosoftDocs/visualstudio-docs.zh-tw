---
title: CA2236 必須：在 ISerializable 類型上呼叫基類方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1d06d4acff24b724388e36de66038f563b1f5dc6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666700"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236：必須呼叫 ISerializable 類型上的基底類別方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別衍生自實作為 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面的型別，且下列其中一個條件成立：

- 型別會實作為序列化的函式，也就是具有 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 的函式，<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 參數簽章，但不會呼叫基底型別的序列化函式。

- 型別會執行 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法，但不會呼叫基底型別的 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法。

## <a name="rule-description"></a>規則描述
 在自訂序列化程式中，型別會執行 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法來序列化其欄位，並使用序列化的函式來還原序列化欄位。 如果型別衍生自實作為 <xref:System.Runtime.Serialization.ISerializable> 介面的型別，則應該呼叫基底型別 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法和序列化的函式，以序列化/還原序列化基底型別的欄位。 否則，類型將不會正確地序列化和還原序列化。 請注意，如果衍生的型別不會加入任何新的欄位，型別就不需要實作為 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法，也不必叫用基底型別對等專案。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請從對應的衍生類型方法或函式，呼叫基底類型 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法或序列化的函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會藉由呼叫序列化的函式和基類的 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> 方法，顯示滿足規則的衍生型別。

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA2240：必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
