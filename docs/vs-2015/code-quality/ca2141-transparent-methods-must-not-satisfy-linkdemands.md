---
title: CA2141：透明方法不能滿足 Linkdemand |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bee810ed938d316e92095ad47062ed5ad9cd456f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546441"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141：透明方法不可以滿足 LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 安全性透明方法會呼叫元件中未以 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 屬性標記的方法，或安全性透明方法會滿足 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` 類型或方法的。

## <a name="rule-description"></a>規則描述
 滿足 LinkDemand 是安全性敏感的作業，可能會導致非預期的許可權提升。 安全性透明程式碼不能滿足 Linkdemand，因為它不受限於安全性關鍵程式碼的相同安全性審核需求。 安全性規則集層級1元件中的透明方法會讓它們滿足的所有 Linkdemand 在執行時間轉換為完整的要求，這可能會導致效能問題。 在安全性規則集層級2元件中，透明方法將無法在即時 (JIT) 編譯器中編譯（如果它們嘗試滿足 LinkDemand）。

 在 usee 層級2安全性的元件中，安全性透明方法嘗試在非 APTCA 元件中滿足 LinkDemand 或呼叫方法時，會引發 a <xref:System.MethodAccessException> ; 在層級1元件中，LinkDemand 會成為完整的要求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請以或屬性標記存取方法 <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> ，或從存取的方法中移除 LinkDemand。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。 這段程式碼將會引發此規則。

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
