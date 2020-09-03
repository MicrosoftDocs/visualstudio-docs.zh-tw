---
title: CA2144：透明程式碼不應該從位元組陣列載入元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 91a846d0f347916a22df54eb1f1a042bc686d132
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546415"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144:透明程式碼不可以從位元組陣列載入組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法會使用下列其中一種方法，從位元組陣列載入元件：

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>規則描述
 透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。 因此，透明程式碼不應該從位元組陣列載入元件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將載入元件的方法標記為 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 此規則會在下列程式碼上引發，因為透明方法會從位元組陣列載入元件。

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2144.transparentmethodsshouldnotloadassembliesfrombytearrays/cs/ca2144 - transparentmethodsshouldnotloadassembliesfrombytearrays.cs#1)]
