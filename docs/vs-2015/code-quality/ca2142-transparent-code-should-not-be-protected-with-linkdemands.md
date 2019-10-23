---
title: CA2142:透明程式碼不應該使用 Linkdemand 來保護 |Microsoft Docs
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
ms.openlocfilehash: a9d8986e9d1e6fc3f614e23fff3f6a24c1cc6e91
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602784"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142:透明程式碼不可以使用 LinkDemand 加以保護
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法需要 <xref:System.Security.Permissions.SecurityAction> 或其他安全性需求。

## <a name="rule-description"></a>規則描述
 需要 LinkDemand 才能存取的透明方法會引發這個規則。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 因為透明方法應該是安全性中性，所以不應進行任何安全性決策。 此外，安全關鍵程式碼（的確會進行安全性決策）不應該依賴透明的程式碼來進行這類決策。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除透明方法上的連結要求，或使用 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性來標記方法（如果它正在執行安全性檢查，例如安全性需求）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，規則會在方法上引發，因為方法是透明的，而且會以包含 <xref:System.Security.Permissions.SecurityAction> 的 LinkDemand <xref:System.Security.PermissionSet> 標示。

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 請勿隱藏此規則的警告。
