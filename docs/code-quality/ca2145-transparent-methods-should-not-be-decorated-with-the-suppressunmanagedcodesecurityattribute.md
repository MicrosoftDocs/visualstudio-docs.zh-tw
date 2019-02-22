---
title: CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9269a0862dacf928cffb31f722f382271d5f0e7
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953850"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因

透明方法，這個方法標記為<xref:System.Security.SecuritySafeCriticalAttribute>方法或包含一種方法的類型以標記<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性。

## <a name="rule-description"></a>規則描述

方法使用裝飾<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性有任何方法呼叫它時放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 標記使用 SuppressUnmanagedCodeSecurity 的方法<xref:System.Security.SecurityCriticalAttribute>屬性會讓這項需求更為明顯的方法呼叫者。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，標記方法，或輸入具有<xref:System.Security.SecurityCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

### <a name="code"></a>程式碼

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]