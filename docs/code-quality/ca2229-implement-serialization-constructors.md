---
title: CA2229:必須實作序列化建構函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d148efb87c8516b34342a8c9d16b63364a2eae16
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231013"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229:必須實作序列化建構函式

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
型別會實<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>作為介面，不是委派或介面，且下列其中一個條件成立：

- 型別沒有接受<xref:System.Runtime.Serialization.SerializationInfo>物件<xref:System.Runtime.Serialization.StreamingContext>和物件（序列化程式的簽章）的函式。

- 類型未密封，且其序列化的存取修飾詞不受保護（系列）。

- 型別是密封的，而且其序列化程式的存取修飾詞不是私用。

## <a name="rule-description"></a>規則描述

此規則與支援自訂序列化的類型有關。 類型支援自訂序列化（如果它會<xref:System.Runtime.Serialization.ISerializable>執行介面）。 序列化（或重新建立）已使用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>方法序列化的物件時，必須要有序列化的函式。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏規則的違規。 此類型不會還原序列化，且在許多情況下都不會運作。

## <a name="example"></a>範例

下列範例顯示符合規則的類型。

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>相關規則

[CA2237：使用 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
