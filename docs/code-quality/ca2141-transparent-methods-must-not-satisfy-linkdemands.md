---
title: CA2141： 透明方法不可以滿足 Linkdemand |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90b1873a13f6e60863a99492c353d2270fdea5e4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141：透明方法不可以滿足 LinkDemand
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 安全性透明方法不以標示之組件中呼叫<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性或安全性透明方法符合<xref:System.Security.Permissions.SecurityAction>`.LinkDemand`類型或方法。  
  
## <a name="rule-description"></a>規則描述  
 滿足 LinkDemand 是安全性敏感作業而造成超過預期的提高權限。 安全性透明程式碼必須不可以滿足 Linkdemand，因為它不受限於相同的安全性稽核需求與安全性關鍵程式碼。 安全性規則集層級 1 組件中的透明方法會導致所有符合要轉換成完整的要求，在執行階段，可能會造成效能問題的 Linkdemand。 在安全性規則集層級 2 組件，透明方法都會失敗當他們嘗試滿足 LinkDemand 在 just-in-time (JIT) 編譯器中編譯。  
  
 在組件中該 usee 層級 2 安全性，嘗試滿足 LinkDemand，或呼叫非 APTCA 組件中的方法的安全性透明方法會引發<xref:System.MethodAccessException>; 層級 1 組件中的 LinkDemand 變成完整的要求。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將標記與的存取方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除存取方法的 LinkDemand。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 在此範例中，透明方法會嘗試呼叫具有 LinkDemand 的方法。 此規則會引發這段程式碼。  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]