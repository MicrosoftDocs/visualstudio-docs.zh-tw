---
title: CA2135:層級 2 組件不應該包含 LinkDemand
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b9e7cb0eba06b00b30c2b7d00fac78206d222f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232236"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135:層級 2 組件不應該包含 LinkDemand

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因
類別或類別成員正在使用層級<xref:System.Security.Permissions.SecurityAction> 2 安全性的應用程式中使用。

## <a name="rule-description"></a>規則描述
LinkDemand 在層級 2 安全性規則集中已被取代。 請使用<xref:System.Security.SecurityCriticalAttribute>屬性來標記方法、類型和欄位，而不是使用 linkdemand 來強制執行即時（JIT）編譯時間的安全性。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請移除<xref:System.Security.Permissions.SecurityAction> ，並將類型或成員<xref:System.Security.SecurityCriticalAttribute>標記為屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在下列範例中， <xref:System.Security.Permissions.SecurityAction>應該移除，且方法會<xref:System.Security.SecurityCriticalAttribute>以屬性標記。

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]