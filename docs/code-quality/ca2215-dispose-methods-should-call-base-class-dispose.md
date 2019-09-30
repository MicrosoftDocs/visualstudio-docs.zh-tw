---
title: CA2215:Dispose 方法應該呼叫基底類別處置
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231286"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215:Dispose 方法應該呼叫基底類別處置

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因
執行的類型會<xref:System.IDisposable?displayProperty=fullName>繼承自<xref:System.IDisposable>也會執行的類型。 繼承類型的<xref:System.IDisposable.Dispose%2A>方法不會呼叫父類型的方法。 <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>規則描述
如果類型繼承自可處置的類型，則必須從本身<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A>的方法中呼叫基底類型的方法。 呼叫基底類型方法 Dispose 可確保釋放基底類型所建立的任何資源。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形， `base`請呼叫。<xref:System.IDisposable.Dispose%2A> 在您<xref:System.IDisposable.Dispose%2A>的方法中。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果呼叫`base`，則可以安全地隱藏此規則的警告。<xref:System.IDisposable.Dispose%2A> 在比規則檢查更深入的呼叫層級發生。

## <a name="example"></a>範例
下列範例顯示的型`TypeA`別<xref:System.IDisposable>會執行。

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>範例
下列範例顯示繼承自類型`TypeB` `TypeA`的類型，並正確地呼叫其<xref:System.IDisposable.Dispose%2A>方法。

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)