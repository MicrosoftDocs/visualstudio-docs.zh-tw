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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
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
 安全性透明方法會呼叫元件中未標記為 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性的方法，或是安全性透明方法會滿足 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` 類型或方法的。

## <a name="rule-description"></a>規則描述
 滿足 LinkDemand 是安全性敏感的作業，可能會導致意外的權限提高。 安全性透明程式碼不能滿足 Linkdemand，因為它不受限於安全性關鍵程式碼的相同安全性審查需求。 安全性規則集層級1元件中的透明方法會使它們滿足的所有 Linkdemand 在執行時間轉換為完整要求，這可能會造成效能問題。 在安全性規則集層級2元件中，如果透明方法嘗試滿足 LinkDemand，就無法在即時（JIT）編譯器中進行編譯。

 在 usee 層級2安全性的元件中，安全性透明方法嘗試滿足 LinkDemand 或呼叫非 APTCA 元件中的方法會引發 <xref:System.MethodAccessException> ; 在層級1元件中，LinkDemand 會變成完整的要求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請使用或屬性來標記存取方法 <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> ，或從存取的方法中移除 LinkDemand。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。 此規則會在此程式碼上引發。

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
