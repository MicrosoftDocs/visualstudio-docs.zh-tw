---
title: CA1403：自動設定類型不應該是 COM 可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534923"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403:自動配置類型不應該是 COM 可見
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見的實數值型別會標示 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 設定為的屬性 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.LayoutKind> 版面配置類型是由 common language runtime 所管理。 這些類型的版面配置可以在 .NET Framework 版本之間變更，這會中斷預期特定配置的 COM 用戶端。 請注意，如果 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 未指定屬性，則 c #、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 和 c + + 編譯器會指定實 <xref:System.Runtime.InteropServices.LayoutKind> 數值型別的配置。

 除非以其他方式標示，否則 COM 會看到所有的公用非泛型型別;COM 看不到所有非公用和泛型型別。 不過，若要減少誤報，此規則需要明確陳述型別的 COM 可見度;包含的元件必須標記 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 為， `false` 而且類型必須標記為，而且必須將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設為 `true` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性的值變更 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 為 <xref:System.Runtime.InteropServices.LayoutKind> 或 <xref:System.Runtime.InteropServices.LayoutKind> ，或讓 COM 看不到該類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別，以及滿足規則的型別。

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱
 [簡介類別介面](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[合格的 .net](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [型別與非受控碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)交互操作的互通性
