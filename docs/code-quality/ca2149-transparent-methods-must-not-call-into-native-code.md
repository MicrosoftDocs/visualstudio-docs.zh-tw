---
title: CA2149:透明方法不可以呼叫機器碼
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4811a117220aa154283d97d44d49a8257c4be86e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031795"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149:透明方法不可以呼叫機器碼

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會呼叫原生的函式，透過例如 P/Invoke 方法 stub。

## <a name="rule-description"></a>規則描述
 任何直接呼叫原生程式碼，例如透過 P/Invoke 的透明方法會引發此規則。 違反此規則會導致<xref:System.MethodAccessException>層級 2 透明度模型，而完整的要求，如<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>層級 1 透明度模型中。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將方法呼叫原生程式碼標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]