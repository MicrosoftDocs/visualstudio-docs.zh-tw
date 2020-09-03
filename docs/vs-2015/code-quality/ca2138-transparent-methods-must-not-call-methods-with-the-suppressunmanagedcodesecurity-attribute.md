---
title: CA2138：透明方法不能使用 SuppressUnmanagedCodeSecurity 屬性來呼叫方法 |Microsoft Docs
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
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546493"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138:透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法會呼叫以屬性標記的方法 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 。

## <a name="rule-description"></a>規則描述
 這項規則會在任何直接呼叫機器碼的透明方法上引發，例如透過 P/Invoke 使用 (平台叫用) 呼叫。 以屬性標記的 P/Invoke 和 COM interop 方法會 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 導致在呼叫方法上執行 LinkDemand。 由於安全性透明程式碼無法滿足 Linkdemand，因此程式碼也無法呼叫以 SuppressUnmanagedCodeSecurity 屬性標記的方法，或以 SuppressUnmanagedCodeSecurity 屬性標記的類別方法。 方法將會失敗，或需要轉換為完整需求。

 違規此規則會導致 <xref:System.MethodAccessException> 層級2安全性透明度模型中的，以及 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 層級1透明度模型中的完整需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性，並將方法標記為 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
