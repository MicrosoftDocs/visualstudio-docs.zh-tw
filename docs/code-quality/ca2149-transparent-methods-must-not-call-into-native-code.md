---
title: CA2149:透明方法不可以呼叫機器碼
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231959"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149:透明方法不可以呼叫機器碼

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|分類|Microsoft.Security|
|重大變更|中斷|

## <a name="cause"></a>原因
方法會透過方法存根（例如 P/Invoke）呼叫原生函式。

## <a name="rule-description"></a>規則描述
此規則會在直接呼叫機器碼（例如透過 P/Invoke）的任何透明方法上引發。 違反此規則會導致層級<xref:System.MethodAccessException> 2 透明度模型中的成為，層級1透明度模型<xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A>中的完整需求。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請將呼叫機器碼<xref:System.Security.SecurityCriticalAttribute>的方法標記為或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]