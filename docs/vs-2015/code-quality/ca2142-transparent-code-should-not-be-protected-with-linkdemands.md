---
title: CA2142： 透明程式碼應該不使用 Linkdemand 加以保護 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 744ca0b6b988591b646c66d349cc39649d323116
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588037"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142：透明程式碼不可以使用 LinkDemand 加以保護
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2142： 透明程式碼不應該使用 Linkdemand 加以保護](https://docs.microsoft.com/visualstudio/code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands)。

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明的方法需要<xref:System.Security.Permissions.SecurityAction>] 或 [其他安全性需求。

## <a name="rule-description"></a>規則描述
 需要 LinkDemand 才能存取的透明方法會引發這個規則。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 應該是中性的安全性透明方法，因為它們應該不會進行任何安全性決策。 此外，安全關鍵程式碼，並做出安全性決策，這應該不會依賴先前已這類決定的透明程式碼。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除透明方法上的連結要求，或標示的方法與<xref:System.Security.SecuritySafeCriticalAttribute>屬性，如果它正在執行安全性檢查，例如安全性需求。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，會引發此規則在方法上因為方法是透明的且標示與 LinkDemand <xref:System.Security.PermissionSet> ，其中包含<xref:System.Security.Permissions.SecurityAction>。

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 請勿隱藏此規則的警告。



