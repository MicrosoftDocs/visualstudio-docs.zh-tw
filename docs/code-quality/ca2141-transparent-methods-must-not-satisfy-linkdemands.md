---
title: CA2141：透明方法不可以滿足 LinkDemand
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a11c5bdf6cd5d2c1e278d7e8943aa672621672cd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551645"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141：透明方法不可以滿足 LinkDemand
|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法不以標示之組件中呼叫方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性或安全性透明方法會滿足<xref:System.Security.Permissions.SecurityAction>`.LinkDemand`類型或方法。

## <a name="rule-description"></a>規則描述
 滿足 LinkDemand 的比較是安全性敏感的作業會導致非預期的提高權限。 安全性透明程式碼必須不可以滿足 Linkdemand，因為它不受限於相同的安全性稽核需求，為安全性關鍵程式碼。 安全性規則集層級 1 組件中的透明方法會導致所有 linkdemand 都會滿足轉換成完整的要求，在執行階段，可能會造成效能問題。 在安全性規則集層級 2 組件，透明方法會失敗當他們嘗試滿足 LinkDemand 在 just-in-time (JIT) 編譯器中編譯。

 使用層級 2 安全性的組件，在安全性透明方法，來滿足 LinkDemand 或非 APTCA 組件中呼叫方法的嘗試會引發<xref:System.MethodAccessException>; 層級 1 組件中 LinkDemand 變成完整的要求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記與存取的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除存取方法的 LinkDemand。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。 此規則會引發這段程式碼。

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]