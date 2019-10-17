---
title: CA1403：自動配置類型不應該是 COM 可見
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8329c51e58478e1902f64232f4f2546418639e34
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440530"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403：自動配置類型不應該是 COM 可見

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|分類|Microsoft. 互通性|
|重大變更|中斷|

## <a name="cause"></a>原因

元件物件模型（COM）可見實數值型別已標記為 <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> 屬性設定為 <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述

<xref:System.Runtime.InteropServices.LayoutKind> 版面配置類型是由 common language runtime 所管理。 這些類型的配置可能會在 .NET 版本之間變更，這會中斷需要特定版面配置的 COM 用戶端。 如果未指定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性，則C#、Visual Basic 和C++編譯器會為實數值型別指定[layoutkind.sequential 標示。](<xref:System.Runtime.InteropServices.LayoutKind.Auto>)

除非另有標記，否則 COM 可以看到所有公用的非泛型型別，而且 COM 看不到所有的非公用和泛型型別。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度。 包含的元件必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 設定為 `false`，而且類型必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `true`。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性的值變更為[layoutkind.sequential 標示](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>)或[layoutkind.sequential 標示](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)，或讓 COM 無法看到此類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的類型，以及符合規則的類型。

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>相關規則

[CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>請參閱

- [限定交互操作的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與非受控程式碼交互操作](/dotnet/framework/interop/index)
