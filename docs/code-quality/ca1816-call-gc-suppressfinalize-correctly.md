---
title: CA1816:正確呼叫 GC.SuppressFinalize
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233535"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816:正確呼叫 GC.SuppressFinalize

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|分類|Microsoft. 使用量|
|重大變更|不中斷|

## <a name="cause"></a>原因

此規則的違規可能是由下列原因所造成：

- 方法，這是的<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>實作為，而且不會呼叫。 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- 不是的實<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>作為，且會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>的方法。

- 呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>並傳遞[此C#（）](/dotnet/csharp/language-reference/keywords/this)或[Me （Visual Basic）](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)以外之專案的方法。

## <a name="rule-description"></a>規則描述

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>方法可讓使用者在物件變成可供垃圾收集之前，隨時釋放資源。 如果呼叫<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>方法，它會釋出物件的資源。 這會導致不必要的終止。 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> ，讓垃圾收集行程不會呼叫物件的完成項。

若要防止具有完成項的衍生型別<xref:System.IDisposable>必須重新叫用並呼叫它，沒有完成項的<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>未密封型別仍應呼叫。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規：

- 如果方法是的執行<xref:System.IDisposable.Dispose%2A>，請新增對的<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>呼叫。

- 如果方法不是的執行<xref:System.IDisposable.Dispose%2A>，請移除對的<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>呼叫，或將它移至類型的<xref:System.IDisposable.Dispose%2A>實作為。

- 將所有呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>變更為，以傳遞[此C#（）](/dotnet/csharp/language-reference/keywords/this)或[Me （Visual Basic）](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果您故意使用<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>來控制其他物件的存留期，則只會隱藏此規則的警告。 如果的<xref:System.IDisposable.Dispose%2A>執行不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>，請勿隱藏此規則的警告。 在此情況下，無法抑制完成會降低效能，且不提供任何好處。

## <a name="example-that-violates-ca1816"></a>違反 CA1816 的範例

此程式碼會顯示呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>的方法，但不會傳遞[此（C#）](/dotnet/csharp/language-reference/keywords/this)或[Me （Visual Basic）](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。 因此，此程式碼違反規則 CA1816。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>滿足 CA1816 的範例

這個範例會示範透過傳遞<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> [this （C#）](/dotnet/csharp/language-reference/keywords/this)或[Me （Visual Basic）](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)正確呼叫的方法。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>相關規則

- [CA2215Dispose 方法應該呼叫基類處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>另請參閱

- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)