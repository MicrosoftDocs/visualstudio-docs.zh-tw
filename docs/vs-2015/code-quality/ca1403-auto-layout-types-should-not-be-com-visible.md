---
title: CA1403:自動配置類型不應該是 COM 可見 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2420582ab342948d7774e1bb9e4b5947f44f8d2b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695433"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403:自動配置類型不應該是 COM 可見
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見實值類型會標示<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>屬性設為<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.LayoutKind> 配置類型是由通用語言執行平台管理。 這些類型的配置可以變更版本之間的.NET Framework 中，將會中斷 COM 用戶端預期特定的版面配置。 請注意，如果<xref:System.Runtime.InteropServices.StructLayoutAttribute>未指定屬性，則C#， [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，和C++指定編譯器<xref:System.Runtime.InteropServices.LayoutKind>實值類型的配置。

 除非已標記，否則所有公用的非泛型型別會顯示為 COM;所有的非公用和泛型型別都看不到 COM 不過，以減少誤判，此規則需要明確指示; 類型的 COM 的可視性包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設定為`false`且型別必須標示有<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將變更的值<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為<xref:System.Runtime.InteropServices.LayoutKind>或<xref:System.Runtime.InteropServices.LayoutKind>，或對 COM 不可見的型別

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型，以及滿足規則的型別。

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱
 [類別介面簡介](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024)[限定互通的.NET 類型](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)[與相互操作 Unmanaged 程式碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
