---
title: CA2120 必須：安全序列化的函數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b734a5de257273312e5125c5f481ff889cd33e0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664760"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120：必須保護序列化建構函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 型別會實作為 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面，不是委派或介面，而且會在允許部分信任呼叫端的元件中宣告。 型別具有接受 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> 物件和 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> 物件（序列化程式的簽章）的函式。 此函式不會受到安全性檢查的保護，但類型中的一或多個一般函式會受到保護。

## <a name="rule-description"></a>規則描述
 此規則與支援自訂序列化的類型有關。 如果類型執行 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> 介面，則支援自訂序列化。 序列化的函式是必要的，可用來還原序列化或重新建立已使用 <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> 方法序列化的物件。 因為序列化的函式會配置並初始化物件，所以在一般的函式上出現的安全性檢查也必須存在於序列化的函式上。 如果您違反此規則，無法以其他方式建立實例的呼叫端可以使用序列化的函式來執行此動作。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用與保護其他的處理常式相同的安全性要求來保護序列化的函數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏規則的違規。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
