---
title: CA2142:透明程式碼不可以使用 LinkDemand 加以保護
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab0f6aaae97a510b0521e10ad607a86988c345a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232088"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142:透明程式碼不可以使用 LinkDemand 加以保護

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因
透明方法需要<xref:System.Security.Permissions.SecurityAction>或其他安全性需求。

## <a name="rule-description"></a>規則描述
此規則會在需要 Linkdemand 才能存取的透明方法上引發。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 因為透明方法應該是安全性中性，所以不應進行任何安全性決策。 此外，安全關鍵程式碼（的確會進行安全性決策）不應該依賴透明的程式碼來進行這類決策。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請移除透明方法的連結要求，或使用<xref:System.Security.SecuritySafeCriticalAttribute>屬性來標記方法（如果它正在執行安全性檢查，例如安全性需求）。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在下列範例中，規則會在方法上引發，因為方法是透明的，而且會以<xref:System.Security.PermissionSet> <xref:System.Security.Permissions.SecurityAction>包含的 LinkDemand 標記。

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

請勿隱藏此規則的警告。