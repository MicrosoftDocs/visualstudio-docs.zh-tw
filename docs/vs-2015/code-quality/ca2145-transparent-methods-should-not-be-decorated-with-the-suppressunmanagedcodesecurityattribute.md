---
title: CA2145：透明方法不應使用 SuppressUnmanagedCodeSecurityAttribute 裝飾 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d5eb16130aef42abcf9fddf533d0253864a75114
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546402"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法、使用方法標記的方法 <xref:System.Security.SecuritySafeCriticalAttribute> ，或包含方法的類型會以 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性標記。

## <a name="rule-description"></a>規則描述
 以屬性裝飾的方法 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 會在呼叫它的任何方法上放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 將使用 SuppressUnmanagedCodeSecurity 的方法標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性，可讓方法的呼叫端更清楚這項需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用屬性來標記方法或類型 <xref:System.Security.SecurityCriticalAttribute> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>註解
