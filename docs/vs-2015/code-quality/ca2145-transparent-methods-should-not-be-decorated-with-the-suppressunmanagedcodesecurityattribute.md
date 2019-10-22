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
ms.openlocfilehash: 6bffa680fa39014ffa96feec997b5eca63ee08ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610215"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145：透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法、以 <xref:System.Security.SecuritySafeCriticalAttribute> 方法標記的方法，或包含方法的類型會標示 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性。

## <a name="rule-description"></a>規則描述
 以 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性裝飾的方法會在呼叫它的任何方法上放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 將使用 SuppressUnmanagedCodeSecurity 的方法標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性，可讓方法的呼叫者更清楚這項需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將方法或類型標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>註解
