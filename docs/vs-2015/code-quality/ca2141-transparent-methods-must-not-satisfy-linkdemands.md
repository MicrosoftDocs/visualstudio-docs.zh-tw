---
title: CA2141： 透明方法不可以滿足 Linkdemand |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7c54b472e91aa2be1d8e5bb1a9c32c26c0cb299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142699"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141：透明方法不可以滿足 LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法不以標示之組件中呼叫方法<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性或安全性透明方法會滿足<xref:System.Security.Permissions.SecurityAction>`.LinkDemand`類型或方法。

## <a name="rule-description"></a>規則描述
 滿足 LinkDemand 的比較是安全性敏感的作業可能會造成非預期的提高權限。 安全性透明程式碼必須不可以滿足 Linkdemand，因為它不受限於相同的安全性稽核需求，為安全性關鍵程式碼。 安全性規則集層級 1 組件中的透明方法會導致所有 linkdemand 都會滿足轉換成完整的要求，在執行階段，可能會造成效能問題。 在安全性規則集層級 2 組件，透明方法會失敗當他們嘗試滿足 LinkDemand 在 just-in-time (JIT) 編譯器中編譯。

 在組件中該 usee 層級 2 安全性、 安全性透明方法，來滿足 LinkDemand 或非 APTCA 組件中呼叫方法的嘗試會引發<xref:System.MethodAccessException>; 層級 1 組件中 LinkDemand 變成完整的要求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記與存取的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除存取方法的 LinkDemand。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。 此規則會引發這段程式碼。

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
