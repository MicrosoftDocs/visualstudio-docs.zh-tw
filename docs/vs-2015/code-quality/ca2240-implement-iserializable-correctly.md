---
title: CA2240： 實作 ISerializable 正確 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8613e4ea5fedec9e5c95d6cfde3a61bc37f2cd92
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272450"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240：必須正確實作 ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的類型是指派給<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面以及其中一個下列條件成立：

-   型別繼承，但不覆寫<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>方法和型別宣告與未標記的執行個體欄位<xref:System.NonSerializedAttribute?displayProperty=fullName>屬性。

-   不密封型別和型別實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>不是外部可見和可覆寫的方法。

## <a name="rule-description"></a>規則描述
 執行個體在繼承的類型中宣告的欄位<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面不會自動包含在序列化程序。 若要加入的欄位，類型必須實作<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>方法和序列化建構函式。 如果欄位不應該序列化，套用<xref:System.NonSerializedAttribute>屬性設為明確指出決策的欄位。

 在未密封的的實作類型<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>應外部可見方法。 因此，方法可以由衍生型別、 呼叫，而且是可覆寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>可見和可覆寫的方法，並確定所有執行個體欄位會包含在序列化程序，或明確標示為<xref:System.NonSerializedAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示兩個違反規則的可序列化型別。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>範例
 下列範例會藉由提供可覆寫 [ISerializable.GetObjectData] 實作修正的兩個先前的違規情事 (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) 上的活頁簿類別並提供的實作<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->程式庫類別上。

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)



