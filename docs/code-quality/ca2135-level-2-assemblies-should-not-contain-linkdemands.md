---
title: CA2135:層級 2 組件不應該包含 LinkDemand
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b306711bac791ff8d460da1f25e8a73c70f388b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069235"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135:層級 2 組件不應該包含 LinkDemand

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 使用 類別或類別成員<xref:System.Security.Permissions.SecurityAction>使用層級 2 安全性的應用程式中。

## <a name="rule-description"></a>規則描述
 LinkDemand 在層級 2 安全性規則集中已被取代。 不使用 Linkdemand 在 just-in-time (JIT) 編譯時間在強制執行安全性，來標記方法、 類型和欄位<xref:System.Security.SecurityCriticalAttribute>屬性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除<xref:System.Security.Permissions.SecurityAction>並標示的型別或成員<xref:System.Security.SecurityCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，<xref:System.Security.Permissions.SecurityAction>應該移除，且方法標示為<xref:System.Security.SecurityCriticalAttribute>屬性。

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]