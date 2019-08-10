---
title: CA2138:透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920584"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138:透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
安全性透明方法會呼叫以<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性標記的方法。

## <a name="rule-description"></a>規則描述
此規則會在任何直接呼叫機器碼的透明方法上引發, 例如使用 P/Invoke (平台叫用) 呼叫。 P/Invoke 和以<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性標記的 COM Interop 方法會導致對呼叫方法執行 LinkDemand。 由於安全性透明程式碼無法滿足 Linkdemand, 因此程式碼也無法呼叫以 SuppressUnmanagedCodeSecurity 屬性標記的方法, 或以 SuppressUnmanagedCodeSecurity 屬性標記的類別方法。 方法將會失敗, 或要求將會轉換成完整的要求。

違反此規則會導致 level 2 <xref:System.MethodAccessException>安全性透明度模型中的成為, 層級1透明度模型<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>中的完整需求。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請移除<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性, 並<xref:System.Security.SecurityCriticalAttribute>使用或<xref:System.Security.SecuritySafeCriticalAttribute>屬性來標記方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]