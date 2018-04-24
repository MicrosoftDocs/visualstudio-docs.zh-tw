---
title: CA2144：透明程式碼不可以從位元組陣列載入組件
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c2ebb4b088a0712773ce8d5c208ba0f921df75
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144：透明程式碼不可以從位元組陣列載入組件
|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法會載入組件從位元組陣列，使用下列方法之一：

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

-   <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>規則描述
 透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。 因此，透明程式碼應該不從位元組陣列載入組件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將方法載入的組件標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 透明方法從位元組陣列載入組件，因為此規則會引發下列程式碼。

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]