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
ms.openlocfilehash: 4e302c9e8cc74d461dc67237bd62b34097c0aceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542179"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138:透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法呼叫的方法，以標記<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性。

## <a name="rule-description"></a>規則描述
 此規則會引發任何透明的方法，直接呼叫原生程式碼，例如，使用 P/Invoke （平台叫用） 呼叫。 P/Invoke 和 COM interop 方法標記著<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性導致進行對呼叫方法的 LinkDemand。 安全性透明程式碼無法滿足 Linkdemand，因為程式碼也不能呼叫標記使用 SuppressUnmanagedCodeSecurity 屬性、 方法或標記使用 SuppressUnmanagedCodeSecurity 屬性的類別的方法。 此方法將會失敗，或要求將會轉換成完整的要求。

 違反此規則會導致<xref:System.MethodAccessException>層級 2 安全性透明度模型，而完整的要求，如<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>層級 1 透明度模型中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性，並將標示的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]