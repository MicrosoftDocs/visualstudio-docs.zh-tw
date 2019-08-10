---
title: CA2141：透明方法不可以滿足 LinkDemand
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24723559988974c51798c3e099ff8c1d86a15db9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920510"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141：透明方法不可以滿足 LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
安全性透明方法會呼叫元件中未標記<xref:System.Security.AllowPartiallyTrustedCallersAttribute>為 (APTCA) 屬性的方法, 或是安全性透明方法會<xref:System.Security.Permissions.SecurityAction> `.LinkDemand`滿足類型或方法的。

## <a name="rule-description"></a>規則描述
滿足 LinkDemand 是安全性敏感的作業, 可能會導致意外的權限提高。 安全性透明程式碼不能滿足 Linkdemand, 因為它不受限於安全性關鍵程式碼的相同安全性審查需求。 安全性規則集層級1元件中的透明方法會使它們滿足的所有 Linkdemand 在執行時間轉換為完整要求, 這可能會造成效能問題。 在安全性規則集層級2元件中, 如果透明方法嘗試滿足 LinkDemand, 就無法在即時 (JIT) 編譯器中進行編譯。

在使用層級2安全性的元件中, 安全性透明方法嘗試滿足 LinkDemand 或呼叫非 APTCA 元件中的方法會引發<xref:System.MethodAccessException>; 在層級1元件中, LinkDemand 會變成完整的要求。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請使用<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性來標記存取方法, 或從存取的方法中移除 LinkDemand。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在此範例中, 透明方法會嘗試呼叫具有 LinkDemand 的方法。 此規則會在此程式碼上引發。

[!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]