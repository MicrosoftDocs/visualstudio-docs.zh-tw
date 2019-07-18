---
title: CA2236:ISerializable 類型上呼叫基底類別方法 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4ec8c14da5c691f6f9740c6df86cb38aeb9fac5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142398"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236:必須呼叫 ISerializable 類型上的基底類別方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別衍生自型別可實作<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面，以及其中一個下列條件成立：

- 型別會實作序列化建構函式，也就是具有建構函式<xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>，<xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>參數簽章，但不會呼叫基底類型的序列化建構函式。

- 型別會實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法，但不會呼叫<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基底類型的方法。

## <a name="rule-description"></a>規則描述
 自訂序列化程序中的型別會實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法，將序列化其欄位和還原序列化欄位的序列化建構函式。 如果類型是衍生自型別可實作<xref:System.Runtime.Serialization.ISerializable>介面，基底型別<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化建構函式應該呼叫來序列化/還原序列化的基底類型的欄位。 否則，型別不會是序列化和還原序列化正確。 請注意，是否衍生的型別未新增任何新的欄位，類型不需要實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法或序列化建構函式或呼叫基底型別對等項目。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫基底型別<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>從對應的方法或序列化建構函式衍生型別方法或建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範衍生的型別符合規則的序列化建構函式和<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>基底類別的方法。

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2240:必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238： 請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237：Serializableattribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239： 必須提供選擇性欄位的還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120： 必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)
