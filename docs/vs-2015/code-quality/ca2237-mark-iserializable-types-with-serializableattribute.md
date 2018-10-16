---
title: Ca2237： 必須以 SerializableAttribute 標記 ISerializable 類型 |Microsoft Docs
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
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 10a8fa5300241326f2af5df847974644bd4fe0d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201483"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237：必須以 SerializableAttribute 標記 ISerializable 類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的型別會實作<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>介面和類型未標示為<xref:System.SerializableAttribute?displayProperty=fullName>屬性。 此規則會忽略其基底型別不是可序列化的衍生型別。

## <a name="rule-description"></a>規則描述
 要由通用語言執行平台辨識為可序列化，類型必須標記為<xref:System.SerializableAttribute>屬性，即使型別會使用透過實作自訂序列化常式<xref:System.Runtime.Serialization.ISerializable>介面。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，套用<xref:System.SerializableAttribute>屬性型別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏這項規則的例外狀況類別的警告，因為它們必須是可序列化，以便跨應用程式定義域正常運作。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。 取消註解<xref:System.SerializableAttribute>屬性符合規則的行。

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240：必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120：必須保護序列化建構函式](../code-quality/ca2120-secure-serialization-constructors.md)



