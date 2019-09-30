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
ms.openlocfilehash: 3cca385c346a7daa8aaddb377f999506ffb1abaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232044"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因

透明方法、使用<xref:System.Security.SecuritySafeCriticalAttribute>方法標記的方法，或包含方法的類型會<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>以屬性標記。

## <a name="rule-description"></a>規則描述

以<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性裝飾的方法會在呼叫它的任何方法上放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 將使用 SuppressUnmanagedCodeSecurity <xref:System.Security.SecurityCriticalAttribute>的方法標記為屬性，可讓方法的呼叫端更清楚這項需求。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請使用<xref:System.Security.SecurityCriticalAttribute>屬性來標記方法或類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

### <a name="code"></a>程式碼

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]