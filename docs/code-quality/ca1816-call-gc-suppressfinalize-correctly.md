---
title: CA1816：正確呼叫 GC.SuppressFinalize
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5c874aac5d84d45159ef7d169ab2749269fa0905
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174227"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816：正確呼叫 GC.SuppressFinalize

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|分類|Microsoft。 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因

違反此規則會造成：

- 是的實作方法<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>並不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>。

- 不是實作的方法<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>並呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>。

- 呼叫的方法<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>，並將傳遞的項目以外[this (C#)](/dotnet/csharp/language-reference/keywords/this)或是[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。

## <a name="rule-description"></a>規則描述

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>方法可讓使用者在任何階段變成可供記憶體回收的物件之前釋出資源。 如果<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>呼叫方法，它會釋出資源的物件。 這可讓完成項不必要。 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>讓記憶體回收行程並不會呼叫物件的完成項。

若要避免使用完成項的衍生的類型不必重新實作<xref:System.IDisposable>並呼叫它，而不需要完成項的非密封的類型仍應該呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形：

- 如果方法是實作<xref:System.IDisposable.Dispose%2A>，將呼叫加入<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>。

- 如果方法不是實作<xref:System.IDisposable.Dispose%2A>，移除對<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>或將它移到別的<xref:System.IDisposable.Dispose%2A>實作。

- 變更所有對<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>傳遞[this (C#)](/dotnet/csharp/language-reference/keywords/this)或是[我 (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

只有隱藏此規則的警告，如果您刻意使用<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>控制其他物件的存留期。 如果實作不隱藏此規則的警告<xref:System.IDisposable.Dispose%2A>不會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>。 在此情況下，無法隱藏最終化會降低效能，並不提供任何好處。

## <a name="example-that-violates-ca1816"></a>違反 CA1816 的範例

此程式碼示範的方法會呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>，但未通過[this (C#)](/dotnet/csharp/language-reference/keywords/this)或是[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。 如此一來，此程式碼違反規則 CA1816。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>滿足 CA1816 的範例

此範例示範的方法也正確地呼叫<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>藉由傳遞[this (C#)](/dotnet/csharp/language-reference/keywords/this)或是[Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me)。

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>相關的規則

- [CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>另請參閱

- [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)