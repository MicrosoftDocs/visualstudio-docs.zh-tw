---
title: CA2138：透明方法不能使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 65e00d319bff3bbfd3c441c6b60ed8a703e69251
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654806"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138：透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法會呼叫以 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性標記的方法。

## <a name="rule-description"></a>規則描述
 此規則會在任何直接呼叫機器碼的透明方法上引發，例如透過 P/Invoke （平台叫用）呼叫來使用。 P/Invoke 和 COM Interop 以 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性標記的方法，會導致對呼叫方法執行 LinkDemand。 由於安全性透明程式碼無法滿足 Linkdemand，因此程式碼也無法呼叫以 SuppressUnmanagedCodeSecurity 屬性標記的方法，或以 SuppressUnmanagedCodeSecurity 屬性標記的類別方法。 方法將會失敗，或要求將會轉換成完整的要求。

 違反此規則會導致 Level 2 安全性透明度模型中的 <xref:System.MethodAccessException>，以及層級1透明度模型中 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完整需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性，並使用 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性來標記方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
