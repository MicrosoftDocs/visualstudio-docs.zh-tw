---
title: CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c3d2fe5c2c4e75376f88af7679f6838561848c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949348"
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