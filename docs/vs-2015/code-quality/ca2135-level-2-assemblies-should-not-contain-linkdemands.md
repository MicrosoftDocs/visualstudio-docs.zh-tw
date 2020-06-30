---
title: CA2135：層級2元件不應該包含 Linkdemand |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cbb68855832e84150b81c8a8a6fde47bf9433edc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547702"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135:層級 2 組件不應該包含 LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類別或類別成員正在使用 <xref:System.Security.Permissions.SecurityAction> 層級2安全性的應用程式中使用。

## <a name="rule-description"></a>規則描述
 LinkDemand 在層級 2 安全性規則集中已被取代。 請使用屬性來標記方法、類型和欄位，而不是使用 Linkdemand 來強制執行即時（JIT）編譯時間的安全性 <xref:System.Security.SecurityCriticalAttribute> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除， <xref:System.Security.Permissions.SecurityAction> 並將類型或成員標記為 <xref:System.Security.SecurityCriticalAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中， <xref:System.Security.Permissions.SecurityAction> 應該移除，且方法會以 <xref:System.Security.SecurityCriticalAttribute> 屬性標記。

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
