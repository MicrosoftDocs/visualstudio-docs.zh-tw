---
title: CA1403：自動配置類型不應該是 COM 可見
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: 056b1d254b8544f9a1f0abe364bcb40f15235e64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31899476"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403：自動配置類型不應該是 COM 可見
|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 元件物件模型 (COM) 可見的實值類型會標示<xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>屬性設為<xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>。

## <a name="rule-description"></a>規則描述
 <xref:System.Runtime.InteropServices.LayoutKind> 版面配置類型是由通用語言執行平台管理。 這些類型的配置可以變更版本之間的.NET Framework 中，將會中斷必須有特定配置的 COM 用戶端。 請注意，如果<xref:System.Runtime.InteropServices.StructLayoutAttribute>未指定屬性，C# 中， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]，並指定 c + + 編譯器<xref:System.Runtime.InteropServices.LayoutKind>配置的實值類型。

 除非已標記，否則所有公用的非泛型型別會顯示 com;所有的非公用與泛型型別是看不到 com。 不過，若要減少誤判，這項規則要求 COM 可見性的明確指示; 類型包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設`false`和型別都必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute>設`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更值<xref:System.Runtime.InteropServices.StructLayoutAttribute>屬性<xref:System.Runtime.InteropServices.LayoutKind>或<xref:System.Runtime.InteropServices.LayoutKind>，或讓型別看不到 com。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型，以及滿足規則的型別。

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>相關的規則
 [CA1408：不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>另請參閱
 [限定互通的.NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [Unmanaged 程式碼的互通](/dotnet/framework/interop/index)