---
title: CA2144:透明程式碼不可以從位元組陣列載入組件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 971c7e794c5b782c2ba71be868fc2f9e7747fdb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542274"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144:透明程式碼不可以從位元組陣列載入組件

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法會載入組件從位元組陣列，使用下列方法之一：

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>規則描述
 透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。 因此，transparent 程式碼應該不從位元組陣列載入組件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記正在載入組件的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 因為透明方法會從位元組陣列載入組件上的下列程式碼會引發此規則。

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]