---
title: CA2229：執行序列化的函數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662837"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229：請實作序列化建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 型別會執行 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面、不是委派或介面，而且下列其中一個條件成立：

- 型別沒有採用 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 物件和 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 物件（序列化程式的簽章）的函式。

- 類型未密封，且其序列化的存取修飾詞不受保護（系列）。

- 型別是密封的，而且其序列化程式的存取修飾詞不是私用。

## <a name="rule-description"></a>規則描述
 此規則與支援自訂序列化的類型有關。 如果類型執行 <xref:System.Runtime.Serialization.ISerializable> 介面，則支援自訂序列化。 若要還原序列化或重新建立已使用 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法序列化的物件，必須要有序列化的函式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏規則的違規。 此類型不會還原序列化，且在許多情況下都不會運作。

## <a name="example"></a>範例
 下列範例顯示符合規則的類型。

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
