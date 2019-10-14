---
title: CA2216:可處置的類型應該宣告完成項
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ac52bdb17aeb7d04e434d2b02ff9a905eab49a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305924"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216:可處置的類型應該宣告完成項

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Category|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

一個型別，它會執行 <xref:System.IDisposable?displayProperty=fullName>，而且有一些欄位會建議使用非受控資源，而不會如 <xref:System.Object.Finalize%2A?displayProperty=fullName> 所述來實作為完成項。

## <a name="rule-description"></a>規則描述

如果可處置的類型包含下列類型的欄位，則會報告此規則的違規：

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請執行呼叫 <xref:System.IDisposable.Dispose%2A> 方法的完成項。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果類型未針對釋放非受控資源的目的而執行 <xref:System.IDisposable>，則可放心地隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反此規則的類型。

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>相關規則

[CA2115：呼叫 GC。使用原生資源時的 KeepAlive @ no__t-0

[CA1816：呼叫 GC。Gc.suppressfinalize 正確 @ no__t-0

[CA1049：擁有原生資源的類型應該是可處置的 @ no__t-0

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)