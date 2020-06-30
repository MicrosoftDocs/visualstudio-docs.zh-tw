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
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
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
 元件物件模型（COM）可見實數值型別已標記為 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 屬性設定為 <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.LayoutKind>版面配置類型是由 common language runtime 所管理。 這些類型的配置可能會在 .NET Framework 版本之間變更，而這會中斷需要特定配置的 COM 用戶端。 請注意，如果 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 未指定屬性，則 c #、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 和 c + + 編譯器會指定實 <xref:System.Runtime.InteropServices.LayoutKind> 數值型別的配置。

 除非另有標示，否則 COM 可以看見所有公用非泛型型別;COM 不會看到所有非公用和泛型型別。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度;包含的元件必須以 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 設定為的標記 `false` ，而且類型必須以設定為的標記 <xref:System.Runtime.InteropServices.ComVisibleAttribute> `true` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將屬性的值變更 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 為 <xref:System.Runtime.InteropServices.LayoutKind> 或 <xref:System.Runtime.InteropServices.LayoutKind> ，或將類型設為不對 COM 可見。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型，以及符合規則的類型。

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱
 [簡介類別介面](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[適用于互通的 .net 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)可[與非受控程式碼互](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)操作
