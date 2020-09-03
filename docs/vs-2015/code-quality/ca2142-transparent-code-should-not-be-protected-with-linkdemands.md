---
title: CA2142：透明程式碼不應使用 Linkdemand 保護 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546428"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142:透明程式碼不可以使用 LinkDemand 加以保護
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法需要 <xref:System.Security.Permissions.SecurityAction> 或其他安全性需求。

## <a name="rule-description"></a>規則描述
 需要 LinkDemand 才能存取的透明方法會引發這個規則。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 因為透明方法應該是安全性中立的，所以不應該進行任何安全性決策。 此外，可進行安全性決策的安全關鍵程式碼，不應該依賴透明程式碼，就能事先做出這類決定。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除透明方法的連結要求，或在 <xref:System.Security.SecuritySafeCriticalAttribute> 執行安全性檢查（例如安全性要求）的情況下，以屬性標示方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，此規則會在方法上引發，因為方法是透明的，而且會以 <xref:System.Security.PermissionSet> 包含的 LinkDemand 標記 <xref:System.Security.Permissions.SecurityAction> 。

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 請勿隱藏此規則的警告。
