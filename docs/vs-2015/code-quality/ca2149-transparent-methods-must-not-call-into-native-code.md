---
title: CA2149：透明方法不能呼叫原生程式碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1852e7a5cbaa2d25f93618b22d01d23e8a953dcb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667440"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149：透明方法不可以呼叫機器碼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法會透過方法存根（例如 P/Invoke）呼叫原生函式。

## <a name="rule-description"></a>規則描述
 任何直接呼叫機器碼的透明方法都會引發此規則，例如透過 P/Invoke。 違反此規則會導致層級2透明度模型中的 <xref:System.MethodAccessException>，以及層級1透明度模型中 <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> 的完整需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將呼叫機器碼的方法標記為 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]
