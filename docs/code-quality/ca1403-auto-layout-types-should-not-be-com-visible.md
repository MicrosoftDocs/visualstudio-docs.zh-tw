---
title: CA1403:自動配置類型不應該是 COM 可見
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
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234826"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403:自動配置類型不應該是 COM 可見

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|分類|Microsoft.Interoperability|
|重大變更|中斷|

## <a name="cause"></a>原因

元件物件模型（COM）可見實數值型別已標記<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>為屬性設定為。 <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>

## <a name="rule-description"></a>規則描述

<xref:System.Runtime.InteropServices.LayoutKind>版面配置類型是由 common language runtime 所管理。 這些類型的配置可能會在 .NET 版本之間變更，這會中斷需要特定版面配置的 COM 用戶端。 如果未指定C# C++ 屬性，、Visual Basic 和編譯器會為實數值型別指定 [LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) 標示。<xref:System.Runtime.InteropServices.StructLayoutAttribute>

除非另有標記，否則 COM 可以看到所有公用的非泛型型別，而且 COM 看不到所有的非公用和泛型型別。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度。 包含的<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>元件必須以設定為`false`的標記，而且類型<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須以設定為`true`的標記。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請將<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性的值變更為[layoutkind.sequential 標示](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>)或[layoutkind.sequential 標示](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)，或讓該類型不會被 COM 隱藏。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的類型，以及符合規則的類型。

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>相關規則

[CA1408請勿使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱

- [限定交互操作的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與非受控程式碼交互操作](/dotnet/framework/interop/index)