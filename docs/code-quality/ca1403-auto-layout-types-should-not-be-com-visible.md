---
title: CA1403:自動配置類型不應該是 COM 可見
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1f713ac012509dd36d483ca354630e125066360b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954535"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403:自動配置類型不應該是 COM 可見

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|類別|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因

元件物件模型 (COM) 可見實值類型會標示<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>屬性設為<xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述

<xref:System.Runtime.InteropServices.LayoutKind> 配置類型是由通用語言執行平台管理。 這些類型的配置可以變更版本之間的.NET Framework 中，這會中斷 COM 用戶端預期特定的版面配置。 如果<xref:System.Runtime.InteropServices.StructLayoutAttribute>未指定屬性，指定 C#、 Visual Basic 和 c + + 編譯器[實](<xref:System.Runtime.InteropServices.LayoutKind.Auto>)實值型別。

除非已標記，否則所有的公用、 非泛型型別為 COM 可見，而所有的非公用和泛型型別看不到 com。 不過，以減少誤判，此規則需要明確指示類型的 COM 的可視性。 包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設定為`false`且型別必須標示有<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`true`。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將變更的值<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性設定為[LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>)或是[LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)，或對 COM 不可見的型別

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的類型，以及滿足規則的型別。

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>相關的規則

[CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱

- [限定互通的.NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [與 unmanaged 程式碼交互操作](/dotnet/framework/interop/index)